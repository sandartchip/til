

# Bag의 원리 

```python

    def _form_bags(self):
        '''
        Data Loading 단계.


        :return: bags_list, labels_list
        '''
        if self.train: # MNIST 데이터 로딩함.
            train_loader = data_utils.DataLoader(datasets.MNIST('../datasets',
                                                                train=True,
                                                                download=True,
                                                                transform=transforms.Compose([
                                                                         transforms.ToTensor(),
                                                                         transforms.Normalize((0.1307,), (0.3081,))])),
                                                 batch_size=self.num_in_train,
                                                 shuffle=False)

            bags_list = []    # store bag of data
            labels_list = []  # store bag of corresponding label of data
            valid_bags_counter = 0 # keep track of the bags being created
            label_of_last_bag = 0 # 이건 뭐임..?

            for batch_data in train_loader:
                numbers = batch_data[0]
                labels = batch_data[1]

            while valid_bags_counter < self.num_bag:
                bag_length = int(self.r.normal(self.mean_bag_length, self.var_bag_length, 1))
                if bag_length < 1:
                    bag_length = 1
                indices = torch.LongTensor(self.r.randint(0, self.num_in_train, bag_length))  # Bag에서 indice는 random으로 추출
                labels_in_bag = labels[indices]  # bag의 label

                if (self.target_number in labels_in_bag) and (label_of_last_bag == 0): # labels_in_bag 안에 타겟 넘버가 있는지 확인하고, 마지막 bag(?)의 index가 0이면
                    labels_in_bag = labels_in_bag >= self.target_number  # ????
                    labels_list.append(labels_in_bag)
                    bags_list.append(numbers[indices])
                    label_of_last_bag = 1
                    valid_bags_counter += 1
                elif label_of_last_bag == 1: # If the label of the last bag is 1 (indicating t he previous bag contained the target number), create a bag without the target number.
                    index_list = []
                    bag_length_counter = 0
                    while bag_length_counter < bag_length:
                        index = torch.LongTensor(self.r.randint(0, self.num_in_train, 1)) # Bag에서 indice는 random으로 추출
                        label_temp = labels[index]
                        if label_temp.numpy()[0] != self.target_number:
                            index_list.append(index)
                            bag_length_counter += 1 # 조건에 맞으면 bag length counter는 플러스됨

                    index_list = np.array(index_list)
                    labels_in_bag = labels[index_list]  # Bag에 들은 index들의 레이블 모음.
                    labels_in_bag = labels_in_bag >= self.target_number
                    labels_list.append(labels_in_bag) # Bag에 들은 label을 Label list에 append 시킴.
                    bags_list.append(numbers[index_list])
                    label_of_last_bag = 0
                    valid_bags_counter += 1  # Valid bag Counter
                else:
                    pass

        else:
            test_loader = data_utils.DataLoader(datasets.MNIST('../datasets',
                                                               train=False,
                                                               download=True,
                                                               transform=transforms.Compose([
                                                                    transforms.ToTensor(),
                                                                    transforms.Normalize((0.1307,), (0.3081,))])),
                                                batch_size=self.num_in_test,
                                                shuffle=False)

            bags_list = []
            labels_list = []
            valid_bags_counter = 0
            label_of_last_bag = 0

            for batch_data in test_loader:
                numbers = batch_data[0]
                labels = batch_data[1]

            while valid_bags_counter < self.num_bag:
                bag_length = int(self.r.normal(self.mean_bag_length, self.var_bag_length, 1))
                if bag_length < 1:
                    bag_length = 1
                indices = torch.LongTensor(self.r.randint(0, self.num_in_test, bag_length))
                labels_in_bag = labels[indices]

                if (self.target_number in labels_in_bag) and (label_of_last_bag == 0):
                    labels_in_bag = labels_in_bag >= self.target_number
                    labels_list.append(labels_in_bag)
                    bags_list.append(numbers[indices])
                    label_of_last_bag = 1
                    valid_bags_counter += 1
                elif label_of_last_bag == 1:
                    index_list = []
                    bag_length_counter = 0
                    while bag_length_counter < bag_length:
                        index = torch.LongTensor(self.r.randint(0, self.num_in_test, 1))
                        label_temp = labels[index]
                        if label_temp.numpy()[0] != self.target_number:
                            index_list.append(index)
                            bag_length_counter += 1

                    index_list = np.array(index_list)
                    labels_in_bag = labels[index_list]
                    labels_in_bag = labels_in_bag >= self.target_number
                    labels_list.append(labels_in_bag)
                    bags_list.append(numbers[index_list])
                    label_of_last_bag = 0
                    valid_bags_counter += 1
                else:
                    pass

        return bags_list, labels_list

    def __len__(self):
        if self.train:
            return len(self.train_labels_list)
        else:
            return len(self.test_labels_list)

    def __getitem__(self, index):
        if self.train:
            bag = self.train_bags_list[index]
            label = [max(self.train_labels_list[index]), self.train_labels_list[index]]
        else:
            bag = self.test_bags_list[index]
            label = [max(self.test_labels_list[index]), self.test_labels_list[index]]

        return bag, label
```
