# keras v 2.0 class_weight



# Tensorflow v1 -> v2 변경
## Tensorflow import v1 -> v2

- from tensorflow.contrib import layers as contrib_layers <br>
-> 변경 : from tensorflow.keras import layers as contrib_layers <br>

- from tensorflow.contrib import tpu as contrib_tpu <br>
-> 제거 <br>

- tf.train.Optimizer <br>
-> 변경 : tf.keras.optimizers.Optimizer <br>

- tf.logging <br>
-> 변경 : tf.compat.v1.logging <br>

- tf.gfile.GFile <br>
-> 변경 : tf.io.gfile.GFile <br>

- tf.contrib.predictor.from_saved_model <br>
 -> 변경 : tf.lite.TFLiteConverter.from_saved_model <br>
 
- Tensorflow 1.X 버전의 contrib은 대체 불가 <br>
https://www.tensorflow.org/guide/migrate?hl=ko <br>