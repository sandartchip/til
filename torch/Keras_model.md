

## Model 

```python

import keras
from keras.layers import Input, Embedding, LSTM, Dense
from keras.models import Model


main_input = Input(shape=(100,), dtype='int32', name='main_input')

x = Embedding(output_dim=512, input_dim=10000, input_length=100)(main_input)

lstm_out = LSTM(32)(x)


auxiliary_input = Input(shape=(5,), name='aux_input')

x = keras.layers.concatenate([lstm_out, auxiliary_input])
x = Dense(64, activation='relu')(x)
x = Dense(64, activation='relu')(x)
x = Dense(64, activation='relu')(x)

main_output = Dense(1, activation='sigmoid', name='main_output')(x)


model = Model(inputs=[main_input, auxiliary_input], outputs=[main_output, auxiliary_output])

model.compile(optimizer='rmsprop', loss='binary_crossentropy', loss_weights=[1., 0.2])
```


참고) https://ballentain.tistory.com/26
