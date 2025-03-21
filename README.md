# radar_sonic
STM32 đọc dữ liệu từ ADC1 (tần số lấy mẫu 240 kHz, lấy 1200 mẫu) sau đó gửi dữ liệu ADC đã lọc sang ESP32 thông qua UART (baudrate: 2MHz, 8N1). 1200 mẫu được chia thành 12 frame, mỗi frame gồm 2 byte header, 2 byte length, 1 byte id, 200 byte payload, 1 byte checksum, 1 byte end frame. 1 byte id dùng để đánh số frame.
ESP32 nhận được, chuyển 1200 dữ liệu thành mảng 120 phần tử mã màu sau đó vẽ các cung tròn lên màn hình TFT có mã màu tương ứng. Màu được lấy từ dải xanh (0x003f) đến đỏ (0xf800).
1200 mẫu lấy từ ADC tương ứng với khoảng cách tối đa khoảng s=1200/240*340/2=850 mm.
Có thể thay tốc độ quét bằng cách thay đổi omega. Dùng file User_Setup.h để cấu hình màn hình TFT.
