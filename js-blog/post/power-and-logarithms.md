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

Vậy khi chúng ta chia lãi càng nhỏ (tới mức 10<sup>-9</sup>), thì chúng ta sẽ đạt được **growth** càng lớn, giá trị này hội tụ lại tại **e** = 2.71828…( ~171% rate per year). **e** được gọi với cái tên: con số của sự tăng tưởng. **e** là kết quả lớn nhất có thể khi áp dụng **lãi kép liên tục** ở mức lãi 100% sau một đơn vị thời gian (lãi kép liên tục là việc chia nhỏ lãi đến mức không thể nhỏ hơn). Và hàm f(x) = e<sup>x</sup>. Một điều tuyệt vời rằng giá trị của f'(x) = e<sup>x</sup>. Một hàm tuyệt vời. Đây là hàm duy nhất tại thời điểm hiện tại có tính chất này. Thực hiện phép log với cơ số e: log<sub>e</sub><sup>x</sup> được gọi là **natural logarithm**.


## Real exponent

Làm sao để tính a<sup>b</sup> với b là số thực? Chúng ta sẽ cần tới phép **natural logarithm**, cơ số a ta có thể biểu diễn dưới dạng e<sup>x</sup> và **natural logarithm** như sau:

<img width="751" alt="Screen Shot 2022-09-04 at 10 15 25 AM" src="https://user-images.githubusercontent.com/56917374/188295507-abd74de3-1831-41b6-abb7-fd639cd8d687.png">

Có vẻ tới đây thì chúng ta sẽ tính e<sup>b ln a</sup> để có được kết quả của a<sup>b</sup> với b là số thực. Nhưng chúng ta lại gặp vấn đề: *ln a* có thể là số thực, và chúng ta lại quay vào vòng lẩn quẩn. Tuy nhiên ta có thể giải quyết vấn đề này nếu như cơ số là e (why it is magical) bằng công thức sau (Khai triển Taylor đối với chuỗi luỹ thừa - nhờ vào tính chất f'(x) = e<sup>x</sup> nên chúng ta mới có công thức này):

<img width="758" alt="Screen Shot 2022-09-04 at 10 18 38 AM" src="https://user-images.githubusercontent.com/56917374/188295594-71803a25-a1ce-4df7-bd0b-7ef1f337b174.png">

```js
function exp(x) {
    // depend ons how many accuracy, we need to specific fixed K, in this example
    let k = 50;
    let factorial = 1;
    let exponent = 1;
    let sum = 1;
    for (let i = 1; i < k; i++) {
        exponent = exponent * x;
        factorial = factorial * i
        sum = sum + exponent / factorial;
    }
    return sum
}
```
Và bây giờ chúng ta tiếp tục hoàn hiện hàm **ln a**. Theo lý thuyết thì **ln a** được định nghĩa là phần diện tích phía dưới đường cong

<img src="https://sonlhcsuit.github.io/p/power/lna_hu455af0b932974b572a26e22dddb95edb_72211_1024x0_resize_box_3.png">


Và làm sao chúng ta tính được nó khi nguyên hàm của ∫ 1/x = ln∣x∣+C . Lại một vòng lẩn quẩn mới chăng? Thực ra là chúng ta sẽ dùng cả kiến thức về chuỗi luỹ thừa, khai triển **Taylor** nữa, phương pháp **tích phân từng phần**, … Kết quả như sau:

<img width="769" alt="Screen Shot 2022-09-04 at 10 27 02 AM" src="https://user-images.githubusercontent.com/56917374/188295786-84d66a84-04a1-4aa0-9a29-520a808c8541.png">

```js
function ln_upper(a) {
    let k = 50;
    let x = 1 - 1 / a;
    let sum = 0;
    let exponent = 1;
    for (let i = 1; i < k; i++) {
        exponent = exponent * x;
        sum = sum + exponent / i
    }
    return sum
}
```
Còn đây là đối với a ≤ 1:

<img src="https://sonlhcsuit.github.io/p/power/lna-proven_hu9e5ee3e7b34ab1644ea84e2afe1ca980_168408_1024x0_resize_box_3.png" />

```js
function ln_lower(a) {
    let k = 50;
    let u = a - 1;
    let sum = 0;
    let exponent = 1;
    for (let i = 1; i < k; i++) {
        exponent = exponent * u;
        sum = sum + (i % 2 == 1 ? 1 : -1) *( exponent / i)
    }
    return sum
}
```

```js
function exp(x) {
    // depend ons how many accuracy, we need to specific fixed K, in this example
    let k = 50;
    let factorial = 1;
    let exponent = 1;
    let sum = 1;
    for (let i = 1; i < k; i++) {
        exponent = exponent * x;
        factorial = factorial * i
        sum = sum + exponent / factorial;
    }
    return sum
}
function ln_upper(a) {
    let k = 50;
    let x = 1 - 1 / a;
    let sum = 0;
    let exponent = 1;
    for (let i = 1; i < k; i++) {
        exponent = exponent * x;
        sum = sum + exponent / i
    }
    return sum
}
function ln_lower(a) {
    let k = 50;
    let u = a - 1;
    let sum = 0;
    let exponent = 1;
    for (let i = 1; i < k; i++) {
        exponent = exponent * u;
        sum = sum + (i % 2 == 1 ? 1 : -1) * (exponent / i)
    }
    return sum
}
function ln(a){
    if (a<0) return NaN
    if (a<=1) return ln_lower(a);
    return ln_upper(a)
    
}

function pow(base,deg){
    if (base == 1 || base == 0) return base;
    if (deg == 0) return 1;
    if (deg == 1) return base;
    if (isNaN(base) || isNaN(deg)) return NaN;
    if (!isFinite(base) || !isFinite(deg)) return Infinity;

    return exp(deg*ln(base));
}
```

Tới đoạn này thì việc cài đặt một hàm trông có vẻ nhỏ như con thỏ, nhưng lại tốn rất nhiều chất xám, và khó khăn khi cài đặt. Chúng ta đã làm được việc đó rồi. (Ít nhất thì độ chính xác của chúng ta chưa cần thiết quá cao khi nói về các kiến trúc mạng)
