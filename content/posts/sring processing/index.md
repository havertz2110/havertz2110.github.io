---
title: "string processing"
description: "something for strings"
summary: "something for string"
categories: ["Note"]
tags: ["note"]
#externalUrl: ""
date: 2023-07-19
draft: false
authors:
  - 4nh
---
Dưới đây ta sẽ tìm hiểu các hàm xử lý chuỗi phổ biến trong ngôn ngữ C và python. Mình sẽ viết các hàm với công dụng khác nhau nhe, nếu bạn cần cho ngôn ngữ khác mà của mình không có thì hãy tự mò cách đổi nha, thanks all!

#  1. strlen()
Hàm `strlen()` (string length) dùng để lấy kích thước chuỗi (là số lượng ký tự của chuỗi).Kích thước của chuỗi thường được dùng trong các vòng lặp lấy từng ký tự của chuỗi. Cú pháp của hàm là:
```cpp
strlen(str);
```


 Trong đó, `str` có thể là một biến chuỗi hoặc một hằng chuỗi thì cũng đều được chấp nhận.

Chương trình dưới đây hiển thị nội dung của một chuỗi trong đó giữa các ký tự được đặt thêm một ký tự '*':
```c
#include<stdio.h>
#include<conio.h>
#include<string.h> 
main() {
    char str[10] = "V1Study";
    int i; /* truy xuất và hiển thị từng ký tự của chuỗi */ 
    for(i = 0; i<strlen(str); i++)
        printf("%c * ", str[i]); return 0; }
```
Kết quả của chương trình trên được minh họa như sau:
```c
V * 1 * S * t * u * d* y *
```
# 2. strcpy()
Hàm ``strcpy()`` (string copy) dùng để gán chuỗi cho chuỗi.

C không cho phép ta gán trực tiếp chuỗi cho chuỗi thông qua toán tử gán (=) vì chuỗi là mảng ký tự. Vì vậy, ta cần phải sử dụng hàm ``strcpy()``. Hàm này có cú pháp như sau:
```cpp
strcpy(str1, str2);
```
, trong đó,`str1` và `str2` đều có thể là các biến chuỗi hoặc hằng chuỗi.

Hàm ``strcpy()`` sẽ gán giá trị của chuỗi str2 cho chuỗi str1, đồng thời trả về chuỗi str1.

Đoạn mã sau đây minh họa việc sử dụng hàm ``strcpy()``. Nó thay đổi tên của một khách sạn và hiển thị tên mới.
```c
#include<stdio.h>
#include<conio.h>
#include<string.h> 
main() { 
    char tenkhachsan1[15] = "BLUE Hotel"; 
    char tenkhachsan2[15] = "GREEN Hotel"; 
    printf("Ten cu cua khach san la \"%s\"\n", tenkhachsan1); /* tiến hành thay đổi tên của khách sạn */ 
    strcpy(tenkhachsan1, tenkhachsan2); /* sau đó hiển thị tên mới */
    printf("Sau khi doi, khach san co ten la \"%s\"\n", tenkhachsan2);
    return 0; 
}
```
Kết quả của chương trình trên được minh họa như sau:
```c
Ten cu cua khach san la BLUE Hotel
Ten moi cua khach san la Green Hotel
```

# 3. strcat()
Hàm `strcat()` (string concatenate) được sử dụng để nối hai chuỗi vào nhau. Cú pháp của hàm là:
```cpp
strcat(str1, str2);
```

Hàm sẽ tiến hành nối chuỗi `str2` vào sau chuỗi `str1` và trả về nội dung của chuỗi `str1` sau khi nối.

Chương trình sau đây nhận vào họ, đệm và tên, sau đó nối chúng với nhau và hiển thị ra họ tên đầy đủ.
```c
#include<stdio.h> 
#include<conio.h> 
#include<string.h> 
main() { 
    char ho[10]; 
    char dem[10];
    char ten[10]; 
 char hovaten[35]="";
    printf("\nMoi nhap ho: "); /* nhập họ */
    gets(ho); /* tiến hành nối họ và chuỗi chứa họ và tên */ 
    strcat(hovaten, ho);
    printf("\nNhap vao dem: "); /* nhập đệm */ 
    gets(dem); /* đưa thêm dấu cách */ 
    strcat(hovaten, " "); /* rồi đưa đệm vào */ 
    strcat(hovaten, dem);
    printf("\nXin moi nhap ten cua ban: "); /* cuối cùng nhập vào tên*/
    gets(ten); strcat(hovaten, " "); /* rồi đưa tên vào */
    strcart(hovaten, ten); /* và hiển thị ra màn hình họ và tên đầy đủ */
    printf("\nHo va ten cua ban la: \"%s\"", hovaten); 
    return 0; 
}
```
# 4. strchr()
Hàm `strchr()` (string character) dùng để tìm kiếm ký tự trong chuỗi. Cú pháp của hàm là:
```cpp
strchr(str, chr);
```

, trong đó,`chr` có thể là một biến ký tự hoặc một hằng ký tự đều được.

Quy cách hoạt động của hàm này là nó sẽ tìm xem trong chuỗi `str` có ký tự `chr` hay không, nếu có thì hàm trả về chuỗi bắt đầu từ vị trí đầu tiên tìm thấy ký tự `chr` cho đến hết chuỗi `str`, ngược lại thì hàm trả về NULL.

Chương trình sau đây xác định liệu ký tự 'a' có xuất hiện trong tên hai thành phố hay không.
```c
#include<stdio.h>
#include<conio.h>
#include<string.h> 
main() {
    char str1[15] = "Ha Noi"; 
    char str2[30] = "Thanh pho Ho Chi Minh"; 
    char chr = 'a'; 
    clrscr(); /* nếu khác NULL tức là tìm thấy chr trong str1 */ 
    if(strchr(str1, chr) != NULL){ /* thì in ra ra thông báo có xuất hiện */ 
        printf("\n'%c' co xuat hien trong chuoi \"%s\"\n",chr,str1); }
    else{ /* nếu không thì thông báo không xuất hiện */ 
        printf("\n'%c' khong xuat hien trong chuoi \"%s\"\n",chr,str1);
    } /* kiểm tra xem 'a' có nằm trong chuỗi thứ hai không */ 
    if(strchr(str2, chr) != NULL) {
        printf("\n'%c' xuat hien trong \"%s\"\n",chr,str2);
    } 
    else{ 
        printf("\n'%c' khong xuat hien trong \"%s\"\n",chr,str2); 
    } 
    return 0;
}
```
# 5. strstr()
Hàm `strstr()` (string string) dùng để tìm kiếm chuỗi trong chuỗi.Cú pháp của hàm là:
```cpp
strstr(Chuỗi1, Chuỗi2)//tìm Chuỗi2 trong Chuỗi1
```
, trong đó nếu không tìm thấy Chuỗi2 trong Chuỗi1t hìhàm trả về giá trị NULL. Ngược lại, hàm sẽ trả về một chuỗi bắt đầu từ vị trí đầu tiên tìm thấy Chuỗi2cho đến hết Chuỗi1. Ví dụ:
```c
/*khai báo các chuỗi*/ 
char s1[10] = "abcdefghi",s2[5] = "cde", s3[5] = "cdf"; 
strstr(s1, s2); //sẽ tìm chuỗi s2 trong chuỗi s1, hàm trả về kết quả là: "cdefghi" strstr(s1, s3);
strstr(s1,s3);//sẽ tìm chuỗi s3 trong chuỗi s1, hàm trả về kết quả là NULL vì trong chuỗi s1 không có chuỗi "cdf"
```
# 6. strcmp()
Hàm `strcmp()` (string compare) dùng để so sánh hai chuỗi với nhau theo tiêu chí so sánhlàthứ tự ký tự trong bảng mã ASCII. Hàm này thường hay được dùng để sắp xếp các chuỗi theo chiều tăng hoặc giảm theo vần A B C, ví dụ như sắp xếp các tên sinh viên, các tên môn học theo trật tự tăng hoặc giảm.Cú pháp sử dụng hàm này là như sau:
```cpp
strcmp(s1, s2)
```
Hàm sẽ trả về một số chính là hiệu của hai ký tự cuối cùng đem so sánh. Cụ thể hàm sẽ trả về giá trị theo các trường hợp sau:

- một số âm (<0) nếu chuỗi s1 **nhỏ hơn** chuỗis2.

- số 0 (==0) nếu chuỗi s1 **giống hệt** chuỗi s2.

- một số dương (>0) nếu chuỗis1 **lớn hơn** chuỗis2.

Quy cách so sánh:

Việc so sánh sẽ bắt đầu từ hai ký tự đầu tiên bên trái của hai chuỗi. Bắt đầu từ bên trái, hàm sẽ lấy từng ký tự của chuỗi `s2` đem so sánh với ký tự ở vị trí tương ứng của chuỗi `s1`. Nếu hai ký tự đem so sánh giống nhau thì sẽ chuyển sang so sánh hai ký tự kế tiếp bên phải.Nếu hai ký tự khác nhau thì lập tức dừng lại và đưa ra kết quả: ký tự nào có thứ tự trong bảng mã ASCII lớn hơn thì chuỗi tương ứng sẽ lớn hơn chuỗi kia.

Chẳng hạn:

Chuỗi "abc" nhỏ hơn chuỗi "abd", vì ký tự 'd' có vị trí lơn hơn ký tự 'c' trong bảng mã ASCII.

Chuỗi "abc" nhỏ hơn chuỗi "abcd".

Chuỗi "An" nhỏ hơn chuỗi "Anh", chuỗi "Anh" nhỏ hơn chuỗi "Binh", ...

Ví dụ:
```c
char s1[5]="Phan", s2[5]="Phi", s3[5]="Phan", s4[7]="Nhuong";
strcmp(s1,s2); //sẽ so sánh s2 với s1, hàm sẽ trả về một số âm (<0) 
strcmp(s1,s3); //hàm trả về 0 
strcmp(s1,s4); //hàm trả về một số dương (>0)
```
Chương trình sau đây so sánh biến `name1` với các biến name2, name3, name4 và hiển thị kết quả của phép so sánh:
```c
#include<stdio.h>
#include<conio.h> 
#include<string.h> 
main() { 
    char str1[15] = "Ha Noi"; 
    char str2[15] = "Da Nang";
    char str3[15] = "Sai Gon";
    char str4[15] = "Ha Noi"; 
    int sosanh; sosanh = strcmp(str1,str2); 
    printf("\n\"%s\" so sanh voi \"%s\" thi tra ve %d\n", str1, str2, sosanh); 
    sosanh = strcmp(str1, str3);
    printf("\n\"%s\" so sanh voi \"%s\" thi tra ve %d\n", str1, str3, sosanh); 
    sosanh = strcmp(str1,str4); 
    printf("\n\"%s\" so sanh voi \"%s\" thi tra ve %d\n", str1, str4, sosanh); 
    return 0; 
}
```
Kết quả:
```cpp
"Ha Noi" so sanh voi "Sai Gon" thi tra ve -11

"Ha Noi" so sanh voi "Ha Noi" thi tra ve 0
```
# 7. strrev()
Hàm `strrev()` (string reverse) dùng để đảo ngược trật tự một chuỗi. Hàm trả về chuỗi đã được đổi ngược.Cú pháp của hàm là:
```cpp
strrev(Chuỗi)
```
Ví dụ, nếu bạn thực hiện lệnh `strrev("Lap trinh vien");`  thì kết quả là chuỗi sẽ đảo ngược thành ``"neiv hnirt paL"``.

# 8. strlwr()
Hàm `strlwr()` (string lowercase) dùng để chuyển các ký tự từ 'A' đến 'Z' trong một chuỗi thành in thường, các ký tự khác không thay đổi.

Ví dụ, câu lệnh strlwr("ABC");sẽ chuyển chuỗi "ABC" thành "abc".

# 9. strupr()
Hàm `strlupr()` (string uppercase) dùng để chuyển các ký tự từ 'a' đến 'z' trong một chuỗi thành in HOA, các ký tự khác không thay đổi.

Ví dụ, lệnh `strupr("vietnam");` sẽ chuyển chuỗi `"vietnam"` thành chuỗi `"VIETNAM"``.

# 10. strncat()
Hàm này dùng để nối n ký tự của chuỗi sau vào sau chuỗi trước. Cú pháp của hàm như sau:

strncat(s1, s2, n)

Theo đó, hàm sẽ nối n ký tự của chuỗi s2 vào sau chuỗi s1.

#include<stdio.h> #include<string.h> main(){ char s1[]="abcd"; char s2[]="1234"; strncat(s1, s2, 2); puts(s1);//Kết quả là: abcd12 return 0; }
11. strncmp()
Hàm này dùng để so sánh n ký tự đầu tiên của hai chuỗi. Cú pháp như sau:
```cpp
strncmp(s1, s2, n)
```
Theo đó, hàm sẽ so sánh n ký tự đầu của hai chuỗi s1 và s2 theo quy cách so sánh giống như hàm `strcmp()`.
```c
#include<stdio.h> 
#include<string.h>
main(){ 
    char s1[]="abcd", s2[]="abde"; 
    printf("%d",strncmp(s1, s2, 2)); //So sánh 2 ký tự đầu của 2 chuỗi, sẽ trả về 0 
    return 0; }
```
12. strncpy()

Cú pháp:
```cpp
strncpy(s1, s2, n)
```
Hàm này dùng để gán n ký tự đầu tiên của chuỗi s2 cho n ký tự đầu tiên của chuỗi s1.
```c
#include<stdio.h>
#include<string.h>
main(){
    char s1[]="abcd"; 
    char s2[]="1234"; 
    strncpy(s1, s2, 2); //gán 2 ký tự đầu tiên của s2 cho 2 ký tự đầu tiên của s1 
    puts(s1);
    //Kết quả của s1: 12cd 
    return 0; }
```
# 13. upper() (python)
Hao hao cái `strupr()` của C, cú pháp:


# 14. capitalize() (python)
Nó in hoa hết các kí tự trong chuỗi, ví dụ:
```c
string="conchim"
print(string.capitalize())
#ra là "CONCHIM"
```
# 15. replace() (python)
Hao hao cái `strcpy()` của C, ở đây nó cũng dùng để thay thế chuỗi.
Cú pháp:
```python
replace('cái cần thay thế', 'chuỗi dùng để thay thế')
```
Ví dụ:
```python
s= 'hello'
print(s.replace('l','(ell)'))
#sẽ ra là: "he(ell)(ell)o"
```

# 16. strip() (python)
Nó giúp bỏ đi khoảng trắng ở đầu và cuối chuỗi, ví dụ:
```python
string= "    conca  "
print(string.strip())
#ra là: "conca"
```

# 17 split() (python)
Cái này thì chia chuỗi thành list, ví dụ:
```python
string="top 10 thang dien"
print(string.split())
#sẽ ra là: ["top","10","thang","dien"]"
```

# 18. join() (python)
Ngược lại với cái số 17 thui



<div class="warning" style="padding: 0.1em; background-color: #1A1F35;">
    <span style="color: #FFFFFF;">
        <p style="margin-top: 1em; text-align: center;">
            <b>Nói về puts() và printf() 1 chút</b>
        </p>
        <p style="margin-left: 1em; color: #FFFFFF;">
            Trong ngôn ngữ lập trình C (và nhiều ngôn ngữ khác), có hai hàm phổ biến để hiển thị dữ liệu ra màn hình: <strong>puts</strong> và <strong>printf</strong>. Dưới đây là sự khác nhau giữa chúng:
            <br>
            <br>
            <strong>puts:</strong>
            <br>
            Hàm puts được sử dụng để hiển thị một chuỗi, và tự động thêm một dòng mới (ký tự xuống dòng) sau khi hiển thị.
            Không cần định dạng chuỗi với các đối số định dạng như %s trong printf.
            Ví dụ: <code>puts("Hello, world!");</code> sẽ hiển thị "Hello, world!" và thêm một dòng mới.
            <br>
            <br>
            <strong>printf:</strong>
            <br>
            Hàm printf mạnh mẽ hơn, cho phép bạn định dạng và hiển thị nhiều kiểu dữ liệu khác nhau (chuỗi, số nguyên, số thực, ...).
            Bạn cần sử dụng các đối số định dạng như %s, %d, %f để chỉ định kiểu dữ liệu và thay thế bằng các giá trị tương ứng.
            Ví dụ: <code>printf("My name is %s and I am %d years old.", "John", 25);</code> sẽ hiển thị "My name is John and I am 25 years old."
            <br>
            <br>
            Tóm lại, hàm puts thường được sử dụng để hiển thị các chuỗi đơn giản với dòng mới kết thúc, trong khi printf cho phép bạn tùy chỉnh định dạng hiển thị dữ liệu với các kiểu khác nhau.
        </p>
        <p style="margin-bottom: 1em; margin-right: 1em; text-align: right; font-family: Georgia;">
        </p>
    </span>
</div>


