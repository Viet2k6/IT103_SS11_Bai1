### 1. Phân tích lỗi kỹ thuật và cơ chế Falsy Value

- **Nguyên nhân lỗi:** Hàm updateDevice sử dụng if (updatedData.isActive) và if (updatedData.powerWatts) để kiểm tra dữ liệu cập nhật. Vì false và 0 là Falsy Value nên các lệnh cập nhật bị bỏ qua, khiến điều hòa không tắt được và công suất đèn không về 0W.

- **Cách khắc phục:** Thay điều kiện if (prop) bằng if (prop !== undefined)để vẫn cập nhật được các giá trị false và 0`

### 2. Test Cases đối chứng

**Test Case 1: Tắt điều hòa phòng khách**

- Dữ liệu đầu vào: targetId = 1, updatedData = { isActive: false }.
- Kết quả sai thực tế: Điều hòa vẫn bật vì false là Falsy Value.
- Kết quả đúng mong đợi: isActive được cập nhật thành false.

**Test Case 2: Hạ công suất đèn ngủ về 0W**

- Dữ liệu đầu vào: targetId = 2, updatedData = { powerWatts: 0 }.
- Kết quả sai thực tế: Công suất vẫn là 25W vì 0 là Falsy Value.
- Kết quả đúng mong đợi: powerWatts được cập nhật thành 0.
