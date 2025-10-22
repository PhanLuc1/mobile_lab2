
# Geo-Notes (Ghi chú theo vị trí)

## Mô tả
Geo-Notes là ứng dụng ghi chú gắn với vị trí GPS, hiển thị các ghi chú trên bản đồ. Người dùng có thể check-in, xem các ghi chú gần mình, lọc theo bán kính, và mở Google Maps để dẫn đường.

## Tính năng
- Check-in: Tạo ghi chú gắn với vị trí hiện tại.
- Danh sách ghi chú: Hiển thị các ghi chú, vị trí, và nút mở bản đồ.
- Bản đồ: Hiển thị các điểm ghi chú trên bản đồ Leaflet.
- Lọc ghi chú theo bán kính.
- Dẫn đường bằng Google Maps.

## Công nghệ sử dụng
- React
- Leaflet (bản đồ)
- Capacitor Geolocation (lấy vị trí GPS trên mobile)
- Tailwind CSS (giao diện)

## Hướng dẫn cài đặt & chạy
1. Cài đặt các package:
   ```bash
   npm install
   npm install leaflet @capacitor/geolocation
   npm install --save-dev @types/leaflet
   ```
2. Chạy ứng dụng trên web:
   ```bash
   npm run dev
   ```
3. Build và chạy trên Android (Ionic/Capacitor):
   ```bash
   npx run start
   npx run start
   Select i or o to run ios and androi
   ```

## Lưu ý khi chạy trên Android
- Đảm bảo đã cấp quyền truy cập vị trí cho app.
- Nếu bản đồ không hiển thị, hãy kiểm tra lại khởi tạo map và quyền truy cập.
- Đã fix khởi tạo map cho Android bằng delay và cleanup.

## Demo
![alt text](Screenshot_20250929_184337.png)
