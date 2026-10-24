# RoadGuard DJI Crack Review — 20 public frames

20 bản sao JPEG đã kiểm tra và che vùng nhận dạng ở kích thước 1920×1080. Ảnh gốc nội bộ và checkpoint không có trong repo này. `manifest.json` ghi SHA-256 của ảnh public, hash nguồn nội bộ, tọa độ vùng che và đường dẫn ảnh. `predictions/v1.json` và `v2.json` là dự đoán trên ảnh gốc; **không phải nhãn GT**.

ChatGPT xem ảnh ở `images/`, đề xuất **chỉ lớp `crack`**, tọa độ `[x_min,y_min,x_max,y_max]` theo pixel gốc 1920×1080, và trả JSON theo `schema/chatgpt_crack_proposal.schema.json`. Bắt đầu từ `schema/example_proposal.json`, điền `frame_id`, `image_sha256` (hash ảnh public trong manifest), `width`, `height`, `boxes`, `notes`. Không đánh dấu `approved` hoặc suy diễn ảnh không có crack từ box rỗng. Vùng bị che là `uncertain`; người duyệt phải kiểm tra ảnh gốc nội bộ trước khi duyệt toàn frame.

Import nội bộ: `python -m tools.review_crack_v1_v2_20 import --input proposal.json --package-manifest PATH_TO_PUBLIC_BUNDLE/manifest.json`. Import chỉ tạo revision `pending_review`, không thay GT đã duyệt. Metric khóa cho tới khi 20/20 frame được người duyệt xác nhận toàn ảnh.

Sau khi repo public được tạo, URL ảnh trực tiếp có dạng `https://raw.githubusercontent.com/OWNER/roadguard-dji-crack-review/main/images/FRAME_ID.jpg`.
