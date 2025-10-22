# 📍 Geo-Notes - Ứng dụng ghi chú theo vị trí GPS

Ứng dụng React Native Expo cho phép bạn tạo ghi chú gắn với vị trí GPS, xem trên bản đồ và dẫn đường bằng Google Maps.

## ✨ Tính năng

- ✅ Check-in và tạo ghi chú tại vị trí hiện tại
- ✅ Hiển thị ghi chú trên bản đồ với marker
- ✅ Danh sách ghi chú với khoảng cách từ vị trí hiện tại
- ✅ Lọc ghi chú theo bán kính (1km, 5km, 10km, 20km, 50km, hoặc tất cả)
- ✅ Mở Google Maps để dẫn đường đến vị trí ghi chú
- ✅ Xóa ghi chú
- ✅ Lưu trữ dữ liệu local (AsyncStorage)
- ✅ Reverse geocoding - hiển thị địa chỉ từ tọa độ GPS

## 🚀 Cài đặt

### 1. Cài đặt dependencies

```bash
# Tạo project mới (nếu chưa có)
npx create-expo-app geo-notes --template blank-typescript
cd geo-notes

# Cài đặt các package cần thiết
npm install expo-router expo-location react-native-maps @react-native-async-storage/async-storage

# Cài đặt NativeWind cho Tailwind CSS
npm install nativewind tailwindcss
npx tailwindcss init
```

### 2. Cấu hình NativeWind

Tạo file `babel.config.js`:

```javascript
module.exports = function (api) {
  api.cache(true);
  return {
    presets: ['babel-preset-expo'],
    plugins: ['nativewind/babel'],
  };
};
```

### 3. Cấu hình Google Maps (cho Android)

Lấy API key từ [Google Cloud Console](https://console.cloud.google.com/):
- Bật Google Maps SDK cho Android
- Tạo API key
- Thêm vào `app.json` trong phần `android.config.googleMaps.apiKey`

### 4. Chạy ứng dụng

```bash
# iOS
npm run ios

# Android
npm run android

# Web (một số tính năng không hoạt động)
npm run web
```

## 📱 Cấu trúc project

```
app/
├── (tabs)/
│   ├── index.tsx          # Màn hình bản đồ
│   ├── notes.tsx          # Danh sách ghi chú
│   └── _layout.tsx        # Tab navigation
├── _layout.tsx            # Root layout
└── add-note.tsx           # Thêm ghi chú (modal)

components/
├── NoteCard.tsx           # Card hiển thị ghi chú
└── FilterRadius.tsx       # Lọc theo bán kính

hooks/
└── useLocation.ts         # Hook lấy vị trí GPS

utils/
├── location.ts            # Tính khoảng cách, mở Google Maps
└── storage.ts             # Lưu/đọc dữ liệu AsyncStorage

constants/
└── types.ts               # TypeScript interfaces
```

## 🎯 Cách sử dụng

1. **Check-in**: Nhấn nút `+` màu xanh ở góc dưới bên phải màn hình bản đồ
2. **Nhập thông tin**: Điền tiêu đề và nội dung ghi chú
3. **Lưu**: Nhấn "Lưu ghi chú" - ghi chú sẽ được tạo tại vị trí GPS hiện tại
4. **Xem trên bản đồ**: Tab "Bản đồ" hiển thị tất cả marker ghi chú
5. **Lọc**: Chọn bán kính để lọc ghi chú gần bạn
6. **Dẫn đường**: Nhấn nút "Chỉ đường" để mở Google Maps
7. **Xóa**: Nhấn nút "Xóa" trên card ghi chú

## 🔧 Permissions cần thiết

### iOS
- Quyền truy cập vị trí khi sử dụng app

### Android
- ACCESS_FINE_LOCATION
- ACCESS_COARSE_LOCATION

## 📦 Dependencies chính

- `expo-location`: Lấy vị trí GPS và reverse geocoding
- `react-native-maps`: Hiển thị bản đồ
- `@react-native-async-storage/async-storage`: Lưu trữ dữ liệu local
- `expo-router`: File-based routing
- `nativewind`: Tailwind CSS cho React Native

## 🐛 Troubleshooting

### Lỗi "Google Maps API key not found"
- Đảm bảo đã thêm API key vào `app.json`
- Build lại ứng dụng: `expo prebuild --clean`

### Không lấy được vị trí
- Kiểm tra quyền truy cập location trong Settings
- Bật GPS/Location Services trên thiết bị
- Thử trên thiết bị thật (simulator có thể không ổn định)

### Marker không hiển thị trên bản đồ
- Kiểm tra dữ liệu ghi chú có tọa độ latitude/longitude hợp lệ
- Zoom bản đồ ra để thấy các marker xa

## 📝 Ghi chú

- Dữ liệu được lưu local trên thiết bị (AsyncStorage)
- Reverse geocoding có thể không hoạt động ở một số khu vực
- Google Maps chỉ hoạt động trên thiết bị có cài Google Maps app

## 🎨 Tùy chỉnh

Bạn có thể tùy chỉnh:
- Màu sắc marker trên bản đồ (pinColor trong MapView)
- Bán kính lọc mặc định (RADIUS_OPTIONS)
- Style của card ghi chú
- Thêm tính năng: chia sẻ ghi chú, xuất dữ liệu, v.v.

## 📄 License

MIT License - Tự do sử dụng cho dự án cá nhân và thương mại.
