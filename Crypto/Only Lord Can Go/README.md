![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/ae934858-01c7-4713-9305-9719f769ff3e)

Mở file main.go:

![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/f682a6cb-b200-4d44-ab9d-3ea8c9f06b95)


Ta thấy chương trình tạo 6 biến a,b,c,d,e,y random trong khoảng (0, m << 31 - 1).

Ném file main.go lên golang compiler trên programiz.com:

![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/416bb98e-265a-4b44-8625-8b4440214c30)


![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/97898354-c453-4b9d-9b96-d594f1f02756)

Ở vòng for thứ nhất, chương trình sẽ tạo cho chúng ta 5 lucky number, mà mỗi lucky number chính = y = (a*d + b*e + c) % m, sau mỗi lần lại gán e = d và d = y. Ở vòng for thứ 2, chương trình cũng thực hiện như vòng for đầu, nhưng lần này, chúng ta sẽ có 23 lần đoán, và phải đoán đúng theo thứ tự lần lượt từ 1-23 thì server mới đưa flag ra cho chúng ta.


Việc của chúng ta là phải biết được chính xác giá trị của y trong 23 lần đoán tiếp theo. Vậy thì trong vòng for, ta chỉ cần in ra các giá trị y đó, rồi ta sẽ nhập lần lượt từng giá trị đó lên server, thì sẽ được flag.

Chạy trên server:

![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/cc4721f9-ccbb-4239-a43c-1259a0c3d5c1)

Ta thấy giá trị của y giống hệt giá trị compile trên programiz.com, tức là chương trình này được compile ở phiên bản cũ, cũng giống với phiên bản được build trên server, nên các số a,b,c,d,e,y được tạo random nhưng thực chất là sinh số không ngấu nhiên, nên giá trị giống như trên server.

Giờ mình sẽ in ra các giá trị a,b,c,d,e,y ở vòng for đầu tiên, rồi dùng Python để in ra các giá trị của y trong 23 lần tiếp theo:

![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/63abcf51-2466-4556-a9a3-b9269c18fe74)

![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/92fd4290-3848-49bd-8bfa-d942832e77e3)

Các giá trị a,b,c,d,e,y ở vòng for đầu tiên, giờ sẽ đem copy nó chạy trên Python:

![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/066fc64a-30e7-486a-97dd-af61839363eb)

Giá trị của y trong 23 lần tiếp theo

Vì 23 cũng không phải là quá nhiều nên chúng ta có thể nhập thủ công trên server:

![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/7f01d1d9-0766-4cf0-a977-623856f68fcd)

![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/27e07cae-7473-4e6f-a324-513cf1f78dab)

![image](https://github.com/m01000xd/KCSC-CTF-2023/assets/122852491/e350f8ba-0587-4dcf-9d6a-a7e9c3a87973)

**Flag:** **KCSC{G0<1.19_1s_sUcK_0r_U_r_h4rd-w0rk1n9_CRYpt0gr4ph3r???}**



