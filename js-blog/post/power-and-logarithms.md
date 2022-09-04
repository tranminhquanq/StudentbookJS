# Power and logarithms

Một trong nhiều vấn đề khá là nan giải (thực ra không phải là nan giải, “người ta” đã giải quyết nó từ lâu rồi - từ này ở đây với ý nghĩa cách tiếp cận khó khăn) trong lập trình, hoặc toán học đó là phép toán luỹ thừa. Một câu hỏi có thể hay được đặt ra đó là: “Làm sao để tính luỹ thừa bậc n của một số bất kỳ?”. Vấn đề trở nên rất đơn giản nếu như chúng ta sử dụng các ngôn ngữ lập trình Javascript, Python, hoặc là các thư viện kèm theo của các ngôn ngữ bậc thấp như math.h của C / cmath của C++. Nhưng trong trường hợp không không thể sử dụng các built-in, chúng ta tính luỹ thừa như thế nào? Để hiểu rõ được việc làm sao chúng ta có thể cài đặt được phép luỹ thừa, ta sẽ cần rất nhiều kiến thức về toán học cơ bản (bên cạnh đó còn)

## Exponent as natural number

Bằng một vài định nghĩa toán học cơ bản, ta biết được rằng phép toán luỹ thừa là việc thực hiện các phép nhân liên tục. Cụ thể hơn, base được nhân với chính bản thân n lần. Phép toán luỹ thừa đồng thời là một ví dụ điển hình về sự tăng trưởng.

 
<img width="156" alt="Screen Shot 2022-09-04 at 9 49 54 AM" src="https://user-images.githubusercontent.com/56917374/188294907-b8f386b9-c238-4620-9ce0-2a0676df0f67.png">

Bằng định nghĩa này, ta có thể tự implement hàm luỹ thừa như sau:
```js
function pow(base,deg){
    let p = 1;
    for(let i=0;i<deg;i++){
        p = p*base
    }
    return p;
}
```

Tuy nhiên hàm luỹ thừa vẫn chưa đủ nếu chỉ có bấy nhiêu, ta cần phải xem xét, bao quát cả các trường hợp đặc biệt như là **NaN, 0, 1, infinity**. Bằng việc thêm các trường hợp đặc biệt, hàm **pow** đã tốt hơn một tí.

```js
function pow(base,deg){
    if (base == 1 || base == 0) return base;
    if (deg == 0) return 1;
    if (deg == 1) return base;
    if (isNaN(base) || isNaN(deg)) return NaN;
    if (!isFinite(base) || !isFinite(deg)) return Infinity;

    let p = 1;
    for(let i=0;i<deg;i++){
        p = p*base
    }
    return p;
}
```

Chúng ta đã implement một hàm luỹ thừa manually mà không dựa vào thư viện. Tuy vậy, thực sự thì hàm luỹ thừa này vẫn còn thiếu sót rất nhiều, cụ thể hơn **Nếu số mũ của chúng ta số thực thì sao?** Hàm **pow** được cài đặt ở trên lại không thể giúp chúng ta, vì chúng ta không thể lặp “số thực” lần được.

## Logarithms

Cái gì cũng có mặt trái của nó, (chỉ có bản mặt của tôi là không có người yêu), ngoại trừ phép **power** thì chúng ta còn có phép toán **logarithm**. Phép toán **logarithm** giúp chúng ta tìm được **exponent** của một số. Tuy nhiên dựa vào những kiến thức hạn hẹp của tôi về toán và cả lập trình thì tôi chưa nghĩ ra cách nào để cài đặt hàm **logarithm** bằng vòng lặp đơn giản như phép luỹ thừa vậy. Chúng ta hãy tìm hiểu một chút về phép **logarithm** và **e** - magical number. **Logarithm** là **inverse function** của **exponential function**.

<img src="https://sonlhcsuit.github.io/p/power/exponential-vs-logarithm.png" width="400" height="400" />

<img width="768" alt="Screen Shot 2022-09-04 at 9 56 12 AM" src="https://user-images.githubusercontent.com/56917374/188295039-696de3cc-14f3-4f02-9479-d02973b040c0.png">

Nhìn vào công thức quen thuộc này thì chúng ta có thể nhận ra rằng là, nếu chúng ta biết cách tính hàm **logarithm** thì mọi chuyện sẽ trở nên dễ dàng khi tìm bậc luỹ thừa. Nhưng mà mọi chuyện đâu có dễ như vậy, bởi vì chúng ta đang giậm chân tại chỗ ở hàm **pow** hiện tại (chỉ có thể tính được nếu bậc luỹ thừa là số nguyên), vậy nên **n** sẽ luôn luôn là số nguyên (với cái cách tính hàm **pow** ở trên đã được mình đề ra). Chúng ta cần một cách tính khác có thể giúp chúng ta tính được **pow** với bậc luỹ thừa là số thực. Thứ giúp chúng ta làm được việc là **e**, và **calculus**.

## Magical number

Tầm quan trọng của **e** trong giải tích thì không ai phải bàn cãi, nó thực sự rất là quan trọng luôn (quan trọng tới mức tôi không thể sống thiếu e). **Vậy e được tìm ra như thế nào và ý nghĩa của e là gì**? Để làm rõ vấn đề này thì chúng ta sẽ nói về **growth - sự tăng trưởng**. Chúng ta sẽ lấy ví dụ về **compound interest** để dễ hình dung hơn về **growth**. Đặc biệt khi tính toán lãi kép thì đơn vị thời gian chúng ta sử dụng là số nguyên với đơn vị thời gian. Chúng ta hãy tìm hiểu một tí, **e là gì và tại sao e lại đặc biệt như vậy**?

<img width="740" alt="Screen Shot 2022-09-04 at 9 59 19 AM" src="https://user-images.githubusercontent.com/56917374/188295098-fa0a65e7-9d18-4001-9032-53532cc9b7a4.png">

- A: Số tiền cuối cùng bạn nhận được
- P: Số tiền ban đầu
- r: Tỉ lệ lãi
- n: Số lần áp dụng lãi kép ()
- t: Thời gian một chu kỳ (áp dụng lãi kép)

Chúng ta sẽ bắt đầu với

- P: 1 ($)
- r: 1 (100%)
- n: 3 (lần)
- t: 1 (năm)

<img width="770" alt="Screen Shot 2022-09-04 at 10 00 25 AM" src="https://user-images.githubusercontent.com/56917374/188295129-c4c9d6f4-0d6d-4ed2-b4a5-506b7ae42352.png">

Nhìn qua hình này ta có thể nhận ra đây vừa là ví dụ của lãi kép, và vừa là ví dụ power 2 với số mũ là số tự nhiên. Tới đây thì chúng ta sẽ bắt đầu chia số mũ thành từng đoạn nhỏ. Chúng ta thay đổi chu kỳ từ 1 năm thành 6 tháng (hoặc 3) tháng và đồng thời chia nhỏ lãi (thay ví 100% cho 1 năm thì sẽ là 50%/6 tháng và 25%/ 3 tháng) kết quả sẽ như sau:

<img width="764" alt="Screen Shot 2022-09-04 at 10 00 48 AM" src="https://user-images.githubusercontent.com/56917374/188295132-8d0e2259-6f97-490d-a3b0-18491fb23e7a.png">

Vậy khi chúng ta chia lãi càng nhỏ (tới mức 10^{-9}10−9)
