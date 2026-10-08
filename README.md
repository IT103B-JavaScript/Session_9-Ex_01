- Xác định lỗi:
    + lỗi 1: 
        => Dòng lỗi: const basePrice = bookingReservation.priceKey;
        => Nguyên nhân: Truy cập thuộc tính động bằng Dot Notation (obj.prop) khi đó là đang so sánh trong thuộc tính có "priceKey" hay không chứ không phải đúng như mục dích ban đầu là lấy giá trị của priceKey
    + Lỗi 2: 
        => Dòng lỗi: 
            if (bookingReservation.checkInHour < 12) {
                surcharge = basePrice * 0.3;
                bookingReservation.surcharge = surcharge;
            }
        => Nguyên nhân: Dòng gán nằm bên trong if nên chỉ khi dòng if đạt điều kiện đúng thì thuộc tính surcharge mới được tạo ra.

- Test Case:

|Trường hợp kiểm thử | Dữ liệu đầu vào | Kết quả sai thực tế | Kết quả mong đợi|
|---|---|---|---|
|Giống như số liệu ban đầu của đề bài (nhận phòng sớm)| + roomPrice = 1500000 <br> + checkInHour = 9 <br> + priceKey = 'roomPrice'| + Phụ thu nhận phòng sớm: NaN <br> + Tổng số tiền thanh toán: NaN| + Phụ thu nhận phòng sớm: 450000 <br> + Tổng số tiền thanh toán: 1950000|
|Trường hợp nhận phòng đúng giờ (không phụ thu)| + roomPrice = 1500000 <br> + checkInHour = 14 <br> + priceKey = 'roomPrice'| + Phụ thu nhận phòng sớm: undefined <br> + Tổng số tiền thanh toán: NaN| + Phụ thu nhận phòng sớm: 0 <br> + Tổng số tiền thanh toán: 1500000|