
![image](https://user-images.githubusercontent.com/15938354/167174373-65c1cf2f-f681-4dce-898b-280e731b691a.png)

- 감마와 크사이를 가지고 A(hidden의 상태전이 matrix), B(hidden에 observed가 종속될 확률 matrix), 파이를 업데이트, 업데이트 된 A, B, 파이로 크사이와 감마를 다시 업데이트한다.

- 감마는,  t시점에서 hidden state i에 있음.
- observation matrix O가 주어졌을 때 t시점의 상태가 (hidden state)Si일 확률

- 크사이는, t시점에서 hidden state i에 있고 t+1 시점에서는 j 번째 hidden state로 감.
- O가 주어졌을 때 t시점의 상태가 Si, t+1 시점에서 상태가 Sj일 확률 

![image](https://user-images.githubusercontent.com/15938354/167166644-651cadd3-de6a-41ad-9370-3f9de652fe7d.png)

## Estep & Mstep
### Estep
- A와 B-> 알파, 베타 계산. -> 알파,베타->감마, 크사이 계산

### Mstep
-업데이트 된 감마, 크사이로 a,b를 업데이트.

- 언제까지? stoping rule이 작용할 때 까지.


- forward probability는 t-1에서 t로, backward probability는 t+1에서 t로.
