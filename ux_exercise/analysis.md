# Bài tập UX: MoMo — Trợ thủ AI Moni
**Sản phẩm:** MoMo — Phân loại chi tiêu tự động + Chatbot tài chính cá nhân

---

## Phần 1 — Khám phá

### Marketing hứa gì?
- **App Store / PR:** "Trợ thủ AI Moni" — quản lý chi tiêu thông minh, tự động phân loại giao dịch (ăn uống, di chuyển, mua sắm, hoá đơn…), chatbot tài chính cá nhân, gợi ý tiết kiệm.
- **Kỳ vọng từ marketing:** AI hiểu mọi giao dịch, phân loại chính xác, trả lời câu hỏi tài chính cá nhân hoá.

### Thực tế khi dùng thử
> *(Ghi chú quan sát khi dùng app — điền sau khi test)*
>
> - [ ] AI phân loại giao dịch có đúng không?
> - [ ] Chatbot Moni trả lời có liên quan không?
> - [ ] Có nút sửa phân loại không? Dễ tìm không?
> - [ ] Khi hỏi ngoài phạm vi (VD: "lãi suất ngân hàng nào cao nhất?") → phản hồi gì?

---

## Phần 2 — Phân tích 4 Paths

### Path 1: Khi AI ĐÚNG ✅
| Câu hỏi | Phân tích |
|----------|-----------|
| User thấy gì? | Giao dịch xuất hiện với icon + label phân loại (VD: 🍜 Ăn uống, 🚗 Di chuyển). Tổng chi tiêu theo danh mục hiện trên dashboard. |
| Hệ thống confirm thế nào? | Phân loại tự động, không hỏi confirm. User thấy kết quả trực tiếp trên lịch sử giao dịch. |
| Nhận xét | Khi đúng, trải nghiệm mượt — user không cần làm gì thêm. Dashboard chi tiêu theo danh mục tạo giá trị ngay lập tức. |

### Path 2: Khi AI KHÔNG CHẮC ❓
| Câu hỏi | Phân tích |
|----------|-----------|
| Hệ thống xử lý thế nào? | **Điểm yếu lớn:** MoMo dường như không có trạng thái "không chắc" — mọi giao dịch đều được gán nhãn, kể cả khi sai. Không có indicator độ tin cậy. |
| Im lặng? Hỏi lại? Alternatives? | Im lặng — gán nhãn luôn, không hỏi user. Không show alternatives. |
| Nhận xét | Thiếu trạng thái trung gian. Lẽ ra giao dịch mơ hồ (VD: chuyển tiền cho bạn — quà tặng hay trả nợ?) nên hỏi user hoặc hiện "Chưa phân loại — bạn muốn gán vào đâu?" |

### Path 3: Khi AI SAI ❌
| Câu hỏi | Phân tích |
|----------|-----------|
| User biết bằng cách nào? | User tự nhận ra khi xem lại — VD: mua sách online bị gán "Ăn uống" vì merchant là "ShopeeFood". |
| Sửa bằng cách nào? | Tap vào giao dịch → chọn lại danh mục (nếu có). Nhưng flow sửa không rõ ràng, ẩn sâu. |
| Bao nhiêu bước? | ~3–4 tap: Lịch sử → Chọn giao dịch → Tìm nút sửa → Chọn danh mục mới. |
| Nhận xét | Cost sửa lỗi khá cao. Nhiều user sẽ không bận tâm sửa → data sai tích luỹ → dashboard mất chính xác → user mất tin dần. |

### Path 4: Khi user MẤT TIN 💔
| Câu hỏi | Phân tích |
|----------|-----------|
| Có exit không? | Không rõ ràng — không có nút "tắt AI phân loại" hay chuyển sang manual mode. |
| Có fallback? | Chatbot Moni có thể gợi ý liên hệ hotline, nhưng không có nút chuyển nhân viên rõ ràng. |
| Dễ tìm không? | Khó. User bị kẹt trong loop AI mà không có lối thoát rõ ràng. |
| Nhận xét | **Path yếu nhất.** Khi user mất tin vào AI phân loại, không có cơ chế recovery. User chỉ có thể bỏ qua tính năng hoàn toàn → mất giá trị sản phẩm. |

### Tổng kết paths

| Path | Chất lượng | Ghi chú |
|------|-----------|---------|
| 1. Đúng | ⭐⭐⭐⭐ | Trải nghiệm tốt khi AI đúng — dashboard hữu ích |
| 2. Không chắc | ⭐⭐ | Không có trạng thái trung gian, gán nhãn bừa |
| 3. Sai | ⭐⭐ | Sửa được nhưng flow ẩn, cost cao |
| 4. Mất tin | ⭐ | **Yếu nhất** — không có exit, không fallback rõ |

---

## Phần 3 — Gap: Marketing vs Thực tế

| Marketing hứa | Thực tế |
|--------------|---------|
| "AI phân loại thông minh" | Phân loại dựa merchant name, không hiểu context → dễ sai với giao dịch đa nghĩa |
| "Quản lý chi tiêu cá nhân hoá" | Dashboard đẹp nhưng dựa trên data có thể sai → insight không đáng tin |
| "Chatbot tài chính" | Trả lời chung chung, chưa cá nhân hoá sâu theo lịch sử chi tiêu thực tế của user |

**Gap lớn nhất:** Marketing tạo kỳ vọng "AI hiểu bạn" nhưng sản phẩm chưa có cơ chế để AI HỌC từ correction của user. Không có feedback loop rõ ràng.

---

## Phần 4 — Sketch: As-is → To-be

### Path được chọn để cải thiện: **Path 4 — Mất tin** (kết hợp cải thiện Path 2 & 3)

### AS-IS (hiện tại) — Vẽ bên TRÁI

```
[Giao dịch mới] → [AI gán nhãn tự động] → [User thấy nhãn]
                                                    |
                                              Nếu sai? ──→ [Phải tự tìm nút sửa]
                                                    |            (ẩn sâu, 3-4 tap)
                                              Sai nhiều lần?
                                                    |
                                              [User bỏ xem dashboard] ← ❌ DEAD END
                                              (không có exit / recovery)
```

**Chỗ gãy:**
- ❌ Không có trạng thái "không chắc"
- ❌ Nút sửa ẩn, cost sửa cao
- ❌ Không có exit khi mất tin
- ❌ AI không học từ correction

### TO-BE (đề xuất) — Vẽ bên PHẢI

```
[Giao dịch mới] → [AI gán nhãn]
                        |
                   Confidence ≥ 80%? ──YES──→ [Gán nhãn + ✓ nhỏ]
                        |                          |
                       NO                    [Swipe để sửa] ← 1 tap
                        |
                   [Highlight vàng: "Đây là ☕ Cafe?"]
                   [Tap để confirm / chọn khác]
                        |
                   User chọn ──→ [✓ "Đã ghi nhận — AI sẽ nhớ lần sau"]
                                        |
                                   [Data → improve model]

+ THÊM: Settings → "Độ chính xác AI"
    → "Tự động phân loại" (mặc định)
    → "Hỏi tôi khi không chắc" 
    → "Tôi tự phân loại" (tắt AI)

+ THÊM: Dashboard → "3 giao dịch AI chưa chắc" banner
    → Tap → review nhanh → swipe phải = đúng, trái = sửa
```

### Thay đổi cụ thể

| Hành động | Chi tiết |
|-----------|---------|
| **Thêm** | Confidence indicator (highlight vàng cho giao dịch AI không chắc) |
| **Thêm** | 1-tap correction: swipe để sửa ngay trên giao dịch |
| **Thêm** | Feedback message: "AI sẽ nhớ lần sau" → xây trust |
| **Thêm** | Settings toggle: 3 mode (tự động / hỏi khi không chắc / manual) |
| **Thêm** | "Review batch" banner trên dashboard cho giao dịch uncertain |
| **Bớt** | Bỏ flow sửa 3-4 tap, thay bằng inline correction |
| **Đổi** | Từ "luôn gán nhãn" → "gán nhãn + hỏi khi không chắc" |

---

## Kết luận

MoMo AI Moni xử lý tốt **happy path** (AI đúng → dashboard đẹp), nhưng thiếu thiết kế cho **uncertainty và failure**. Đây là pattern phổ biến: team build xong 80% (phân loại hoạt động) nhưng 20% còn lại (sửa lỗi, recovery, feedback loop) mới quyết định user có tin và dùng lâu dài không.

**Một câu tóm gọn:** MoMo cần chuyển từ "AI luôn đúng" sang "AI biết mình có thể sai và giúp user sửa dễ dàng."

---

*Bài tập UX — Ngày 5 — AI in Action · VinUniversity 2026*
