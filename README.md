# שאלה 1
___
### שלב א׳

השיחה עם chatGPT:
<center><iframe width="800" height="600" src="https://chat.openai.com/share/2f5a54f1-054a-4f23-bfca-501c3288d16e"></iframe></center>


הקוד שקיבלתי מchatGPT:

```java
public class TimeComplexityExercise {
    public static void main(String[] args) {
        for (int i = 0; i < N; i += 2) {
            System.out.println("Hello world");
        }

        for (int i = 0; i < Math.sqrt(N); i++) {
            for (int j = 0; j < N; j += 3) {
                System.out.println("Hello world");
            }
        }

        for (int i = 0; i < Math.log(N); i++) {
            for (int j = 0; j < Math.pow(N, 0.25); j++) {
                System.out.println("Hello world");
            }
        }

        for (int i = 0; i < N; i *= 3) {
            System.out.println("Hello world");
        }

        for (int i = 0; i < Math.sqrt(N); i++) {
            for (int j = 0; j < Math.sqrt(N); j++) {
                System.out.println("Hello world");
            }  
        }
    }
}
```

### שלב ב׳

חישוב פונקציית זמן ריצה

|             loop              |    inner loop    | line                                          |     | 
|:-----------------------------:|:----------------:| --------------------------------------------- | --- |
|            N/2 + 1            |                  | for (int i = 0; i < N; i += 2) {              |     |
|              N/2              |                  | System.out.println("Hello world");            |     |
|          sqrt(N) + 1          |                  | for (int i = 0; i < Math.sqrt(N); i++) {      |     |
|     sqrt(N) `*` (N/3 + 1)     |      N/3+1       | for (int j = 0; j < N; j += 3) {              |     |
|        sqrt(N) `*` N/3        |       N/3        | System.out.println("Hello world");            |     |
|          log(N) + 1           |                  | for (int i = 0; i < Math.log(N); i++) {       |     |
| log(N) `*` (pow(N, 0.25) + 1) | pow(N, 0.25) + 1 | for (int j = 0; j < Math.pow(N, 0.25); j++) { |     |
|    log(N) `*` pow(N, 0.25)    |   pow(N, 0.25)   | System.out.println("Hello world");            |     |
|         log_3(N) + 1          |                  | for (int i = 1; i < N; i `*`= 3) {            |   changed i = 1 for valid loop condition   |
|           log_3(N)            |                  | System.out.println("Hello world");            |     |
|          sqrt(N) + 1          |                  | for (int i = 0; i < Math.sqrt(N); i++) {      |     |
|   sqrt(N) `*` (sqrt(N) + 1)   |   sqrt(N) + 1    | for (int j = 0; j < Math.sqrt(N); j++) {      |     |
|      sqrt(N) `*` sqrt(N)      |     sqrt(N)      | System.out.println("Hello world");            |     |

<center><iframe width="800" height="600" src="https://chat.openai.com/share/d8234381-d901-4595-81b4-3ddc9125e582"></iframe></center>

---
$$\text{T(N)} = (\frac{N}{2} + 1 + \frac{N}{2})  + ((\sqrt{N} + 1) + (\sqrt{N} \cdot (\frac{N}{3} + 1)) + (\sqrt{N} \cdot \frac{N}{3})) + ((\log{N} + 1) + (\log{N} \cdot (\sqrt[4]{N} + 1)) + (\log{N} \cdot \sqrt[4]{N})) + ((\log_3{N} + 1) + \log_3{N}) + ((\sqrt{N} + 1) + (\sqrt{N} \cdot (\sqrt{N} + 1)) + (\sqrt{N} \cdot \sqrt{N}))
$$
$$
	\text{T(N)} = (N+1)+\left( \left( 2+\frac{2\cdot N}{3} \right)\cdot \sqrt{ N }+1 \right)+(2\cdot\log N\cdot(1+\sqrt[4]{N})+1)+ (2\cdot \log_3{N}+1)+(2\cdot\sqrt{ N }+2\cdot N+1)
$$
$$
  \text{T(N)} = \sqrt{ N } \cdot\left( 2+\frac{2\cdot N}{3} \right)+2\cdot \log N\cdot(1+\sqrt[4]{ N })+2\cdot \log_3{N}+2\cdot \sqrt{ N }+3N+5
$$

### שלב ג׳

חישוב חסם עליון של פונקציית זמן ריצה:
<center><iframe width="800" height="600" src="https://chat.openai.com/share/9282e3c8-0746-4946-9219-f65d91937870"></iframe></center>
$$
  \text{T(N)} = \sqrt{ N } \cdot\left( \cancel{ 2 }+\frac{2\cdot N}{3} \right)+2\cdot \log N\cdot(\cancel{ 1 }+\sqrt[4]{ N })+2\cdot \log_3{N}+2\cdot \sqrt{ N }+3N+5
$$
$$
\text{T(N)}=\cancel{ \frac{2}{3} }\cdot N^{1.5}+\cancel{ 2\cdot \log N\cdot \sqrt[4]{ N } }+\cancel{ 2\cdot \log_3{N} }+\cancel{ 2\cdot \sqrt{ N } }+\cancel{ 3N }+\cancel{ 5 }
$$
$$
O(N^{1.5})
$$


# שאלה 2
---
### שלב א׳

<center><iframe width="800" height="600" src="https://chat.openai.com/share/53132c7e-1b75-4c82-9864-05b07cd73b8a"></iframe></center>

---
$$
f(x)=x^3+ 2⋅e^x+ log(x)      
$$
$$
f(x)=3x^2−\frac{e ^{2x }}{x}​+log2​(x!)
$$
$$
f(x)=\sqrt{ x }+e^{2x}\cdot \log_{10}{(x+1)}
$$
$$
f(x)=\frac{e^x}{x^2+1}+\log_3{(x!)}-x^3
$$
$$
f(x)=\frac{x^4}{4!}+3\cdot \ln (x+2)+e^{0.5x}
$$
$$
f(x)=\frac{e^x-e^{-x}}{2x}+\ln(2x^2+1)
$$$$
f(x)=2x^3+\frac{e^{0.5x}}{\sqrt{ x }}-\log_2{(x!)}
$$
$$
f(x)=\ln(x^2+1)+\frac{e^{2x}}{2x}-\frac{x^3}{e!}
$$
$$
f(x)=4x^4 -e^{0.5x}\cdot \ln(x+3)-\frac{1}{x!}
$$
$$
f(x)=\frac{e^x}{x^2}+\frac{x^3}{3!}-\log_{e^2}{(x+1)}
$$
### שלב ב׳

<center><iframe width="800" height="600" src="https://chat.openai.com/share/ec22937e-1c1c-411f-9e8e-5490796ec3c2"></iframe></center>

---
$$
f(x)=\cancel{ x^3 }+C2⋅e^x+\cancel{ log(x) }
$$
$$O(e^x)$$
---
$$
f(x)=\cancel{ 3x^2 }−\frac{e ^{2x }}{x}​+\cancel{ log2​(x!) }
$$
$$O(e^{2x})$$
---
$$
f(x)=\cancel{ \sqrt{ x } }+e^{2x}\cdot \log_{10}{(x+1)}
$$
$$O(e^{2x})$$
---
$$
f(x)=\frac{e^x}{x^2+1}+\cancel{ \log_3{(x!)} }-\cancel{ x^3 }
$$
$$O(e^x)$$
---
$$
f(x)=\cancel{ \frac{x^4}{4!} }+\cancel{ 3\cdot \ln (x+2) }+e^{0.5x}
$$
$$O(e^{0.5x})$$
---
$$
f(x)=\frac{e^x-e^{-x}}{2x}+\cancel{ \ln(2x^2+1) }
$$
$$O(e^x)$$
---
$$
f(x)=\cancel{ 2x^3 }+\frac{e^{0.5x}}{\sqrt{ x }}-\cancel{ \log_2{(x!)} }
$$
$$O(e^{0.5x})$$
---

$$
f(x)=\cancel{ \ln(x^2+1) }+\frac{e^{2x}}{2x}-\cancel{ \frac{x^3}{e!} }
$$
$$O(e^{2x})$$
---

$$
f(x)=\cancel{ 4x^4  }-e^{0.5x}\cdot \ln(x+3)-\cancel{ \frac{1}{x!} }
$$
$$O(e^{0.5x})$$
---

$$

f(x)=\frac{e^x}{x^2}+\cancel{ \frac{x^3}{3!} }-\cancel{ \log_{e^2}{(x+1)} }
$$
$$O(e^x)$$
---

### שלב ג׳

<center><iframe width="800" height="600" src="https://chat.openai.com/share/669089ce-e0d7-4062-ac3a-250566dc6ef2"></iframe></center>

---
1. $$O(e^{0.5x})$$
2. $$O(e^x)$$
3. $$O(e^{2x})$$



# שאלה 3
---

### שלב א׳

<center><iframe width="800" height="600" src="https://chat.openai.com/share/fc15cafc-8b15-4383-a316-09a441924fb3"></iframe></center>

סיכום:
כאשר אלגוריתם עובר **כל** המערך המקרה הטוב והרע יהיו בדרך כלל שווים.

---
### שלב ב׳

<center><iframe width="800" height="600" src="https://chat.openai.com/share/d85f1094-3690-4f57-a045-9909a6dbaca0"></iframe></center>


