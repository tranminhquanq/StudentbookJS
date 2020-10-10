# Cat and Mouse

Có hai chú mèo đứng ở hai vị trí bất kỳ đang nhăm nhe một con chuột, cả hai đều muốn bắt được con chuột này. Được biết tốc độ của hai chú mèo đều tương đương nhau và xuất phát cùng lúc, hãy cho biết chú mèo nào sẽ bắt được con chuột trước.

### Chú ý:

- Nếu cả hai chú mèo đều bắt được chú chuột cùng lúc, chú chuột sẽ thoát được, khi đó hãy trả về `"The mouse has escaped"`
- Vị trí của các con vật được thể hiện bằng các mốc giá trị trên trục số.

### Ví dụ:

```js
function whoWouldWin(cat_a, mouse, cat_b) {
  // do something
  return result;
}

who_would_win(-5, 2, 10); // return "Cat A";
who_would_win(3, 5, 5); // return "Cat B";
who_would_win(6, 3, 6); // return "The mouse has escaped";
```

# Covid19

Cho mảng `arr` gồm các mảng số nguyên chứa id của những người tiếp xúc với nhau qua mỗi lần tiếp xúc. Để thuận tiện cho việc phòng chống `covid-19`, bạn hãy viết chương trình đếm số lượng các trường hợp `F1, F2, F3, F4`.

Biết rằng `0` là id của người bị nhiễm covid 19 (F0), mỗi người sẽ có một id khác nhau, thứ tự các lần tiếp xúc theo sự xuất hiện trong arr và:

- F1 là người tiếp xúc với F0
- F2 là người tiếp xúc với F1
- F3 là người tiếp xúc với F2
- F4 là người tiếp xúc với F3

```js
function covid19(arr) {
  // do something
  return result;
}
```

### Ví dụ:

- Với arr = [
  [0,1,2,3],
  [3,4],
  [3,4,5]
  ]

```js
covid19(arr); // return [3,2,0,0]
// Giải thích: F1 : 1,2,3.F2 : 4,5
```

- Với arr = [
  [0,2,3,4,5],
  [0,1],
  [0,6],
  [1,9,8,7,10],
  [10,11],
  [11,12],
  [12,13]
  ]

```js
covid19(arr); // return [6,4,1,1]
// Giải thích: F1 : 1,2,3,4,5,6. F2 : 7,8,9,10. F3 : 11. F4 : 12.
```

# Sock Merchant 2

Bạn là một chủ cửa hàng vớ (tất) vừa mới nhập về một lô hàng socks với các lượng tất theo danh sách sizes được khách hàng đặt trước. Nhưng vì một số lý do bất khả kháng mà các size tất trong socks bị lẫn lộn với nhau, hơn nữa số lượng cũng thiếu hoặc dư ra rất nhiều, hãy cho biết bạn có thể bán được tối đa bao nhiêu đôi tất trên từng size với lô hàng vừa nhập về.

[socks](https://s3.amazonaws.com/hr-challenge-images/25168/1474122392-c7b9097430-sock.png)

```js
function saleMerchandise(socks, sizes) {
  // do something
  return result;
}
```

### Ví dụ:

- Với socks = [1, 2, 3, 1, 2, 4], sizes = [1, 2, 4]

```js
saleMerchandise(socks, sizes); // return [1, 1, 0]
```

- Giải thích: Với sizes[i] = 1 thì trong socks có 1 đôi có size bằng 1, tương tự với sizes[i] = 2 cũng có 1 đôi, còn với sizes[i] = 4 thì không có đôi nào.

# factorialDivisible

Cho một số nguyên `n` và biểu thứ `L=(n - 1)! + 1 = 1*2*3...*(n-1) + 1` hãy xác định xem `L` có chia hết cho `n` không.

```js
function factorialDivisible(n) {
  // do something
  return result;
}
```

### Ví dụ:

- Với n = 3

```js
factorialDivisible(n); // return true
// Giải thích: L = 2! + 1 = 1*2 + 1 = 3 chia hết cho 3.
```

- Với n = 5

```js
factorialDivisible(n); // return true
// Giải thích: L = 4! + 1 = 1*2*3*4 + 1 = 25 chia hết cho 5.
```

- Với n = 4

```js
factorialDivisible(n); // return false
// Giải thích: L = 3! + 1 = 6 + 1 = 7 không chia hết cho 4.
```
