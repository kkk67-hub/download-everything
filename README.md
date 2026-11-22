# Download Everything

CLI cho Mac để tải clip TikTok và Instagram theo link hoặc theo dõi profile. yt-dlp tải clip theo link và quét profile TikTok. gallery-dl quét tab Reels của profile Instagram.

Mỗi thành viên clone repo rồi cài các công cụ bên dưới. Danh sách profile, lịch tự tải, nhật ký và video được lưu riêng trên từng máy.

```bash
brew install yt-dlp gallery-dl ffmpeg
```

Tải một hoặc nhiều clip bằng link thật.

```bash
./social-download download 'https://www.tiktok.com/@USER/video/VIDEO_ID' \
  'https://www.instagram.com/reel/REEL_ID/'
```

Thêm profile, quét thử, rồi bật lịch mỗi giờ.

```bash
./social-download watch 'https://www.tiktok.com/@USER' 'https://www.instagram.com/USER/'
./social-download sync
./social-download schedule --minutes 60
```

Lần quét đầu có thể tải cả clip cũ. Các lần sau dùng archive để bỏ qua clip đã tải. Tải Reel theo link và quét profile Instagram dùng hai archive riêng. Nếu quét profile Instagram gặp lỗi `401`, hãy kiểm tra quyền xem profile và cấu hình phiên đăng nhập cục bộ của gallery-dl. Lượt chạy theo lịch ghi kết quả từng profile vào nhật ký.

Thư mục dữ liệu mặc định là `~/Library/Application Support/SocialDownload`. Mở bằng `open "$HOME/Library/Application Support/SocialDownload"`. Video nằm trong `videos`, các profile nằm trong `profiles.txt` và nhật ký của lịch tự tải nằm trong `sync.log`. Xóa dòng tương ứng khỏi `profiles.txt` để ngừng theo dõi một profile.

Chạy `./social-download unschedule` để tắt lịch. Nếu chỉnh sửa mã CLI, chạy lại `schedule` để cập nhật bản chạy nền.
