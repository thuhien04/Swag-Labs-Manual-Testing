# Manual Testing Project — Swag Labs (Sauce Demo)

## Tổng quan dự án

Dự án này thể hiện quy trình kiểm thử thủ công (Manual Testing) cho ứng dụng web thương mại điện tử **[Swag Labs (Sauce Demo)](https://www.saucedemo.com)**, bao gồm thiết kế test case, thực thi kiểm thử và báo cáo lỗi.

Luồng kiểm thử chính: Đăng nhập → xem danh mục sản phẩm → thêm vào giỏ hàng → thanh toán.

---

## Mục tiêu

- Xác minh các chức năng hoạt động đúng theo yêu cầu nghiệp vụ.
- Phát hiện, ghi nhận và theo dõi lỗi trong quá trình kiểm thử.
- Kiểm tra các trường hợp hợp lệ và không hợp lệ.
- Xây dựng tài liệu kiểm thử rõ ràng, đầy đủ và có thể tái sử dụng.

---

## Phạm vi kiểm thử

**Trong phạm vi (In scope):**

  * Đăng nhập (Login)
  * Sản phẩm & Chi tiết sản phẩm (Product & Product Detail)
  * Giỏ hàng (Shopping Cart)
  * Thanh toán (Checkout)
  * Điều hướng & Phiên đăng nhập (Navigation & Session)

**Ngoài phạm vi (Out of scope):**

  * Kiểm thử hiệu năng (Performance Testing)
  * Kiểm thử bảo mật (Security Testing)
  * Kiểm thử tự động (Automation Testing)
  * Kiểm thử ứng dụng di động (Mobile Application Testing)

---

## Môi trường kiểm thử

| Hạng mục | Thông tin |
| --- | --- |
| Hệ điều hành | Windows 11 |
| Trình duyệt | Google Chrome (v156) |
| URL | https://www.saucedemo.com |

## Tài khoản kiểm thử Swag Labs

| Username | Mục đích sử dụng |
| --- | --- |
| `standard_user` | Kiểm thử luồng nghiệp vụ chuẩn |
| `locked_out_user` | Kiểm thử tài khoản bị khóa |
| `problem_user` | Kiểm thử lỗi hiển thị và chức năng |
| `error_user` | Kiểm thử lỗi thao tác và nhập liệu |
| `visual_user` | Kiểm thử lỗi giao diện và dữ liệu hiển thị |

---

## Các trang được kiểm thử

| Trang | URL | Mô tả |
| --- | --- | --- |
| Login | `/` | Đăng nhập bằng username/password, thông báo lỗi |
| Products (Inventory) | `/inventory.html` | Danh sách sản phẩm, sắp xếp, thêm vào giỏ hàng |
| Product Detail | `/inventory-item.html?id={id}` | Xem chi tiết một sản phẩm, thêm/xóa khỏi giỏ hàng |
| Your Cart | `/cart.html` | Xem giỏ hàng, xóa sản phẩm, chuyển sang thanh toán |
| Checkout: Your Information | `/checkout-step-one.html` | Form thông tin người mua |
| Checkout: Overview | `/checkout-step-two.html` | Tóm tắt đơn hàng, chi tiết giá |
| Checkout: Complete | `/checkout-complete.html` | Thông báo thành công, quay lại danh sách sản phẩm |

---

## Cấu trúc dự án

```text
📁 Swag-Labs-Manual-Testing/
├── 📁 Screenshots/      # Bằng chứng hình ảnh tương ứng với từng lỗi
├── 📁 Test_Cases/       # File thiết kế bảng Test Case chi tiết
│   └── 📄 Test_Cases.xlsx
├── 📁 bug-reports/      # Báo cáo chi tiết từng lỗi (Bug Reports)
│   ├── BUG-001-...md
│   └── ...
└── 📄 README.md         # Tài liệu tổng quan dự án
```

---

## Thiết kế test case

Test case được thiết kế theo từng module với cấu trúc thống nhất:

| Cột | Mô tả |
| --- | --- |
| TC ID | Mã test case |
| Module | Module được kiểm thử |
| Test Title | Tiêu đề test case |
| Pre-condition | Điều kiện cần có trước khi thực hiện |
| Test Steps | Các bước thực hiện |
| Test Data | Dữ liệu kiểm thử |
| Expected Result | Kết quả mong đợi |
| Actual Result | Kết quả thực tế |
| Priority | Mức độ ưu tiên |

**Số lượng test case theo module:**

| Module | Số lượng |
| --- | :---: |
| Login | 12 |
| Product | 15 |
| Cart | 12 |
| Checkout | 23 |
| Navigation | 6 |
| **Tổng cộng** | **68** |


---

## Kỹ thuật thiết kế test case

  * Phân vùng tương đương (Equivalence Partitioning)
  * Phân tích giá trị biên (Boundary Value Analysis)
  * Kiểm thử chuyển trạng thái (State Transition Testing)
  * Đoán lỗi (Error Guessing)

---

## Quản lý và báo cáo lỗi

Cấu trúc mỗi báo cáo lỗi bao gồm:
- **Bug ID:** Mã định danh lỗi.
- **Bug Title:** Tiêu đề ngắn mô tả lỗi.
- **Environment:** Môi trường kiểm thử.
- **Steps to Reproduce:** Các bước tái hiện.
- **Expected Result:** Kết quả mong đợi.
- **Actual Result:** Kết quả thực tế phát sinh lỗi.
- **Severity:** Mức độ nghiêm trọng của lỗi.
- **Priority:** Mức độ ưu tiên xử lý lỗi.
- **Attachments:** Bằng chứng hình ảnh/video minh họa lỗi.

### Danh sách lỗi đã ghi nhận (12 Bugs)

| Bug ID | Tiêu đề lỗi | Account | Severity | Priority |
| :---: | :--- | :--- | :---: | :---: |
| [BUG-001](./bug-reports/BUG-001-product-image-mismatch.md) | [Product] Ảnh sản phẩm hiển thị sai cho toàn bộ sản phẩm | `problem_user` | Medium | P2 |
| [BUG-002](./bug-reports/BUG-002-product-sort-not-working.md) | [Product] Bộ lọc sắp xếp sản phẩm không hoạt động | `problem_user` | Medium | P2 |
| [BUG-003](./bug-reports/BUG-003-wrong-product-detail.md) | [Product Detail] Nhấn vào sản phẩm tại trang Products mở sai trang chi tiết | `problem_user` | High | P1 |
| [BUG-004](./bug-reports/BUG-004-checkout-empty-cart.md) | [Cart] Hệ thống cho phép thanh toán và hoàn tất đơn hàng khi giỏ hàng trống | `standard_user` | High | P1 |
| [BUG-005](./bug-reports/BUG-005-add-to-cart-partial-failure.md) | [Product] Nút Add to cart không hoạt động với một số sản phẩm | `problem_user` | High | P1 |
| [BUG-006](./bug-reports/BUG-006-remove-from-cart-not-working.md) | [Product] Nút Remove không hoạt động khi nhấn xóa sản phẩm khỏi giỏ hàng | `error_user` | Medium | P2 |
| [BUG-007](./bug-reports/BUG-007-invalid-product-still-actionable.md) | [Product Detail] Sản phẩm không tồn tại vẫn hiển thị nút Add to cart | `standard_user` | Medium | P3 |
| [BUG-008](./bug-reports/BUG-008-inconsistent-product-image.md) | [Product Detail] Ảnh sản phẩm ở trang Product Detail khác với ảnh ở trang Products | `visual_user` | Medium | P2 |
| [BUG-009](./bug-reports/BUG-009-inconsistent-product-price.md) | [Product] Giá các sản phẩm trên trang Products thay đổi sau mỗi lần tải lại | `visual_user` | High | P1 |
| [BUG-010](./bug-reports/BUG-010-about-link-404.md) | [Navigation] Liên kết About trong Sidebar menu mở trang lỗi 404 | `problem_user` | Medium | P2 |
| [BUG-011](./bug-reports/BUG-011-finish-button-not-working.md) | [Checkout] Nút Finish không hoạt động, không hoàn tất được đơn hàng | `error_user` | Critical | P1 |
| [BUG-012](./bug-reports/BUG-012-last-name-overwrites-first-name.md) | [Checkout] Nhập Last Name bị ghi đè vào First Name, không thể tiếp tục thanh toán | `problem_user` | Critical | P1 |

> Xem toàn bộ tài liệu báo cáo lỗi tại thư mục **[bug-reports/](./bug-reports/)** và bằng chứng hình ảnh tại **[Screenshots/](./Screenshots/)**.
