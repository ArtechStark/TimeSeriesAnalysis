���гɹ�
https://yq.aliyun.com/articles/68463
http://blog.csdn.net/a819825294/article/details/54376781
https://github.com/jaungiers/LSTM-Neural-Network-for-Time-Series-Prediction


def build_model(layers):
    model = Sequential()

    model.add(LSTM(
        input_shape=(timesteps, data_dim),  #(50,1)
        output_dim=50, #��һ��LSTM��Ԫ��������㶨�壬��һ����50 ��������64 128...
        return_sequences=True))
    model.add(Dropout(0.2))

    model.add(LSTM(
        layers[2],  #100, ��һ��LSTM��Ԫ����
        return_sequences=False))
    model.add(Dropout(0.2))

    model.add(Dense(
        output_dim=layers[3])) #1 һ�������Ԥ��
    model.add(Activation("linear"))

    start = time.time()
    model.compile(loss="mse", optimizer="rmsprop")
    print("> Compilation Time : ", time.time() - start)
    return model
	
	
	LSTM(128, input_shape=(timesteps, data_dim)