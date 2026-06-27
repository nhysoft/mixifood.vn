# Demo Day Submission — AI Grading Copilot

---

## Mô tả chi tiết

## 1. Tổng Quan Dự Án

**AI Grading Copilot** giải quyết bài toán chấm bài tự luận viết tay tại các trường THCS Việt Nam. Giáo viên hiện mất 10–15 phút để chấm và viết nhận xét cho mỗi bài — với hàng trăm bài mỗi tuần, đây là gánh nặng thực sự. Hệ thống tự động hoá toàn bộ quy trình: học sinh chụp ảnh bài viết tay → OCR bóc tách chữ → AI chấm theo Rubric → giáo viên duyệt trong 30 giây.

## 2. Vấn Đề Đang Giải Quyết

* Giáo viên THCS chấm 100–300 bài tự luận/tuần, mỗi bài mất 10–15 phút
* Phản hồi chậm 3–7 ngày khiến học sinh không kịp sửa lỗi
* Chấm tay thiếu nhất quán khi giáo viên mệt mỏi

## 3. Giải Pháp — Pipeline 3 Bước

1. **Chụp ảnh** — Học sinh chụp bài viết tay, ảnh được nén ngay trên trình duyệt trước khi gửi
2. **AI xử lý** — Google Cloud Vision OCR bóc tách chữ viết tay → LangGraph Agent điều phối → Gemini 1.5 Flash chấm điểm theo từng tiêu chí Rubric JSONB
3. **Giáo viên duyệt** — Xem điểm đề xuất, chỉnh sửa nếu cần, phê duyệt → Học sinh nhận kết quả trong dưới 1 phút

## 4. Tính Năng Chính

* **OCR chữ viết tay tiếng Việt** chuyên biệt cho giấy kẻ ô ly với Google Cloud Vision
* **Chấm theo Rubric JSONB** — minh bạch, nhất quán, có nhận xét chi tiết từng tiêu chí
* **Human-in-the-loop** — AI chỉ đề xuất điểm, giáo viên là người quyết định cuối cùng
* **Async pipeline** — Upstash QStash xử lý bất đồng bộ, không block server
* **Real-time status** — Short polling 5 giây, học sinh thấy kết quả ngay khi xong

## 5. Tech Stack

* **Backend:** FastAPI · Python 3.12 · LangGraph · SQLModel · Alembic · PostgreSQL
* **AI / OCR:** Gemini 1.5 Flash · Google Cloud Vision API
* **Frontend:** Next.js 16 · TypeScript · Shadcn/ui · Zustand · Tailwind CSS
* **Hạ tầng:** Supabase S3 · Upstash QStash · Docker · Render Free Tier

## 6. Kết Quả Đạt Được

* ⏱ Giảm thời gian chấm từ **10–15 phút/bài** xuống còn **dưới 1 phút**
* 📬 Học sinh nhận phản hồi trong **vài phút** thay vì cả tuần
* 💰 Chạy hoàn toàn **miễn phí** trên Render Free Tier (512MB RAM)
* ✅ Pipeline ổn định với 15+ unit test và E2E test tự động

---

## Link ảnh thumbnail

```
https://www.mixifood.vn/demoday.png
```
