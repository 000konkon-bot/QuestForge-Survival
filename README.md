# Quest Forge - Survival
**Phát triển Quest Forge: hệ thống phân phối nhiệm vụ động cho game 2D dựa trên luật suy diễn từ dữ liệu telemetry**

**Đồ án chuyên ngành CMP436 · Khoa Công nghệ thông tin · HUTECH · HK1 2026–2027**

## Câu định vị
Đồ án giải quyết tình trạng người chơi từ bỏ game do nhiệm vụ mất cân bằng độ khó cho nhóm người chơi game 2D sinh tồn, đo bằng tỉ lệ hoàn thành nhiệm vụ và số chuỗi chết liên tiếp.

## Vấn đề nghiên cứu
Trong các game 2D sinh tồn, hệ thống nhiệm vụ cố định thường không theo kịp sức mạnh thực tế của người chơi. Đồ án xây dựng một hệ chuyên gia (Rule-based Engine) liên tục đọc dữ liệu telemetry để tự động chọn nhiệm vụ vừa sức. Người thiết kế game có thể tinh chỉnh các bộ luật này qua file cấu hình.

## Câu hỏi nghiên cứu và giả thuyết
- **CH1:** Phân phối nhiệm vụ theo luật đọc từ telemetry có đưa tỉ lệ hoàn thành nhiệm vụ vào vùng 60–80% tốt hơn danh sách nhiệm vụ cố định không?
- **CH2:** Cách phân phối đó có giảm số lần chết liên tiếp (≥3 lần trong 5 phút) không?
- **H1:** Tỉ lệ hoàn thành nhiệm vụ của nhóm B nằm trong 60–80%, nhóm A lệch khỏi vùng này ít nhất 15 điểm %.
- **H2:** Số chuỗi chết liên tiếp trung bình mỗi người ở nhóm B thấp hơn nhóm A ít nhất 30%.

## Thiết kế thí nghiệm
- **Nhóm A:** Nhận danh sách nhiệm vụ cố định (Hard-coded).
- **Nhóm B:** Nhận nhiệm vụ phân phối động dựa trên bộ luật (Rule-based).
- **Biến thay đổi duy nhất:** Cơ chế giao nhiệm vụ (đổi qua cờ cấu hình).
- **Mục tiêu mẫu:** ≥20 người chơi (nhóm A ≥8, nhóm B ≥12).

## Bảng trước – sau

| Chỉ số | Cách đo | Trước (Kế hoạch) | Sau (Mục tiêu) | Ngày đo | Bằng chứng |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Tỉ lệ hoàn thành nhiệm vụ** | (Số Quest hoàn thành / Tổng Quest nhận) * 100% | Nhóm A: Chưa có | Nhóm B nằm trong 60–80%, Nhóm A lệch ít nhất 15 điểm % | Nhóm A: W5–W6, Nhóm B: W7 | Đo tự động bằng Telemetry (Google Sheets) |
| **2. Số chuỗi chết liên tiếp** | Đếm số chuỗi HP=0 (≥3 lần/5 phút) của mỗi user | Nhóm A: Chưa có | Nhóm B thấp hơn nhóm A ≥30% | Nhóm A: W5–W6, Nhóm B: W7 | Đo tự động bằng Telemetry (Google Sheets) |

## Sản phẩm dự kiến (MVP)
1. **Gameplay cốt lõi:** Nhân vật 2D di chuyển, chiến đấu, nhặt vật phẩm cộng chỉ số trực tiếp (không túi đồ).
2. **Rule-Based Engine:** Máy luật đọc chỉ số sức mạnh của người chơi để rẽ nhánh nhiệm vụ phù hợp.
3. **Telemetry:** Tự động gửi log sự kiện về server.
4. **DevSecOps:** API Server bằng Python (FastAPI), chạy trên Docker, có CI/CD.

## Công nghệ sử dụng
- **Client:** Unity 2D (C#)
- **Server:** Python FastAPI
- **DB/Log:** Google Sheets API, Discord Webhook
- **DevSecOps:** Docker, GitHub Actions, Render

## Tiến độ 10 Tuần
- **W1:** Đề cương, Repo, Chốt Pilot
- **W4:** Must #1 (Core game, gửi sự kiện telemetry)
- **W5:** Must #2 (Máy luật A/B, Google Sheets)
- **W6:** Must #3 (Bảng tổng hợp chỉ số)
- **W7:** Docker + CI/CD
- **W10:** Bản v1.0, Video demo, Báo cáo cuối

## Dữ liệu người chơi
Dữ liệu Telemetry chỉ được thu thập khi người chơi đồng ý và hoàn toàn ẩn danh.

## Thông tin sinh viên
- **Sinh viên:** Ngô Thành Tiến · MSSV 2380602230 · Lớp 23DTHC7
- **GVHD:** TS. Nguyễn Quang Trung
