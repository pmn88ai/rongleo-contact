📇 Danh Bạ Cá Nhân V5 — README
🎯 Mục tiêu

Web app quản lý danh bạ cá nhân:

1 file duy nhất (index.html)
Không build, không npm
Sync đa thiết bị (Supabase)
Dùng ngay, mở là chạy
🚀 Cách chạy (2 phút)
1. Tạo Supabase project
Vào: https://supabase.com
Create project
2. Tạo table

Vào SQL Editor, paste đoạn SQL trong cuối file (Claude đã để sẵn)

👉 Bấm Run

3. Lấy API key

Vào:

Settings → API

Copy:

Project URL
anon public key
4. Dán vào file

Tìm 2 dòng:

const SUPABASE_URL = "YOUR_SUPABASE_URL"
const SUPABASE_KEY = "YOUR_SUPABASE_ANON_KEY"

👉 thay bằng của mày

5. Chạy

Chỉ cần:

double click index.html

👉 xong, dùng luôn

🧠 Kiến trúc
🔐 Isolation (bắt buộc)
const USER_ID = "RongLeo"
const APP_ID  = "danh_ba"

Mọi query đều:

.eq("id_user", USER_ID)
.eq("id_app", APP_ID)

👉 Không bao giờ lẫn data app khác

🗄️ Database

1 table duy nhất: contacts

phones → jsonb
emails → jsonb
socials → jsonb
specs → jsonb
lists → jsonb

👉 Không join, không phức tạp

🔄 Sync
Load: Supabase
Fail → localStorage
Khi tab active lại → auto reload
window.addEventListener("focus", reloadData)
💾 Save
1. upsert Supabase
2. save localStorage (backup)
📱 Tính năng chính
👤 Contact model

Một người có thể có:

nhiều số điện thoại
nhiều email
nhiều social (Zalo, FB, Telegram)
nhiều chuyên môn
nhiều list
✏️ Form
Dynamic add/remove
Tag style (Enter để thêm)
Dropdown + tạo mới
🔍 Tìm kiếm & lọc
theo tên / SĐT / org
theo chuyên môn
theo list
theo mức độ quan hệ
📥 Import

Hỗ trợ:

JSON
CSV
VCF (vCard)
Logic:
Dedup: name + phone
Mode:
Skip
Overwrite
📤 Export
JSON
full backup
giữ nguyên structure
CSV
flatten data
mở Excel được
VCF (quan trọng)
multiple phone
multiple email
social → URL

👉 import vào iPhone / Android OK

⚠️ Lưu ý quan trọng
❌ Không có push trực tiếp vào danh bạ điện thoại

👉 Cách đúng:

Export .vcf
Mở trên điện thoại
Import
⚠️ Không dùng realtime
không websocket
không channel

👉 chỉ pull-on-focus

⚠️ Data safety
luôn filter id_user + id_app
không overwrite nhầm
🧪 Debug nhanh
Không thấy data?

👉 check:

đã dán đúng API chưa
đã tạo table chưa
Sync không chạy?

👉 thử:

reload tab
chuyển tab rồi quay lại
Import lỗi?

👉 kiểm tra:

file encoding UTF-8
CSV delimiter (, hoặc ;)
📦 Deploy
Cách đơn giản:
upload file lên:
Vercel
Netlify
GitHub Pages

👉 chạy như web bình thường

🐉 Triết lý app này
Không framework
Không over-engineer
1 file duy nhất
Data là trung tâm
Sync nhẹ, đủ dùng
🔮 Hướng nâng cấp (nếu thích)
nhắc lịch follow-up
tag AI gợi ý quan hệ
auto enrich contact (email → info)