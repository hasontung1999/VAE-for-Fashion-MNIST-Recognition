# VAE-for-Fashion-MNIST-Recognition
Xây dựng Encoder cho VAE có một số khác biệt so với AE, layer cuối cùng trong Encoder là Dense(latent_dim) với latent_dim=128, output của layer cuối này ở VAE được dùng làm mean và log_sigma để xác định latent code theo phân phối Gaussian và đồng thời, nó cũng được sử dụng để tính loss KL Divergence.
Hàm loss được xây dựng cho việc train VAE:
+ binary crossentropy: hàm này thể hiện được sự khác biệt trong phân phối của dữ liệu.
+ KL divergence: hàm này giúp dữ liệu tuân theo phân phối Gaussian.

Sau khi train xong VAE thì sẽ sử dụng lại Encoder ghép với một model có tác vụ phục vụ cho việc nhận diện thời trang MNIST. (set Encoder.variable_trainable về false để tránh train lại).
Xây dựng hàm loss và accuracy cho việc train cả mô hình:
  + Loss: categorical_crossentropy, hàm loss này giúp đánh giá so với one-hot.
  + Metrics: sử dụng metrics accuracy của tensorflow keras.
