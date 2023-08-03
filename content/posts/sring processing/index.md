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
Dưới đây ta sẽ tìm hiểucác hàm xử lý chuỗi phổ biếntrong ngôn ngữ C.

1. strlen()
Hàm strlen() (string length) dùng để lấy kích thước chuỗi (làsố lượng ký tự của chuỗi).Kích thướccủa chuỗi thường được dùng trong cácvòng lặp lấy từng ký tự củachuỗi. Cú pháp của hàm là:

strlen(str);

, trong đó,strcó thể là một biến chuỗi hoặc một hằng chuỗi thì cũng đều được chấp nhận.

Chương trình dướiđây hiển thị nội dung của một chuỗi trong đó giữa các ký tự được đặt thêm một ký tự '*':

#include<stdio.h> #include<conio.h> #include<string.h> main() { char str[10] = "V1Study"; int i; /* truy xuất và hiển thị từng ký tự của chuỗi */ for(i = 0; i<strlen(str); i++) printf("%c * ", str[i]); return 0; }
Kết quả của chương trình trên được minh họa như sau:

V * 1 * S * t * u * d* y *

2. strcpy()
Hàm strcpy() (string copy) dùng để gán chuỗi cho chuỗi.

Ngôn ngữC không cho phép ta gán trực tiếp chuỗi cho chuỗi thông qua toán tử gán (=) vì chuỗi là mảng ký tự. Vì vậy, ta cần phải sử dụng hàm strcpy(). Hàm này có cú pháp như sau:

strcpy(str1, str2);

, trong đó,str1vàstr2đều có thể là các biến chuỗi hoặc hằng chuỗi.

Có thể bạn quan tâm
Mỗi múi giờ cách nhau bao nhiêu km?
Một cái bánh chưng rán bao nhiêu calo?
Từ Hậu Giang đến An Giang bao nhiêu km
Tôi cần những giấy tờ gì để đăng ký vào trường đại học 2023?
Đạp xe bao nhiêu km một ngày là đủ?
Hàm strcpy() sẽ gán giá trị của chuỗi str2 cho chuỗi str1, đồng thời hàmtrả về chuỗi str1.

Đoạn mãsau đây minh họa việc sử dụng hàm strcpy(). Nó thay đổi tên của một khách sạn và hiển thị tên mới.

#include<stdio.h> #include<conio.h> #include<string.h> main() { char tenkhachsan1[15] = "BLUE Hotel"; char tenkhachsan2[15] = "GREEN Hotel"; printf("Ten cu cua khach san la \"%s\"\n", tenkhachsan1); /* tiến hành thay đổi tên của khách sạn */ strcpy(tenkhachsan1, tenkhachsan2); /* sau đó hiển thị tên mới */ printf("Sau khi doi, khach san co ten la \"%s\"\n", tenkhachsan2); return 0; }
3. strcat()
Hàm strcat() (string concatenate)được sử dụng để nối hai chuỗi vào nhau. Cú pháp củahàm là:

strcat(str1, str2);

Hàm sẽ tiến hành nối chuỗi str2 vào sau chuỗi str1 vàtrả về nội dung của chuỗi str1 sau khi nối.

Chương trình sau đây nhận vào họ, đệmvà tên, sau đónối chúng với nhau và hiển thị ra họ tên đầy đủ.

#include<stdio.h> #include<conio.h> #include<string.h> main() { char ho[10]; //họ char dem[15]; //đệm char ten[10]; //tên char hovaten[35]=""; printf("\nMoi nhap ho: "); /* nhập họ */ gets(ho); /* tiến hành nối họ và chuỗi chứa họ và tên */ strcat(hovaten, ho); printf("\nNhap vao dem: "); /* nhập đệm */ gets(dem); /* đưa thêm dấu cách */ strcat(hovaten, " "); /* rồi đưa đệm vào */ strcat(hovaten, dem); printf("\nXin moi nhap ten cua ban: "); /* cuối cùng nhập vào tên*/ gets(ten); strcat(hovaten, " "); /* rồi đưa tên vào */ strcart(hovaten, ten); /* và hiển thị ra màn hình họ và tên đầy đủ */ printf("\nHo va ten cua ban la: \"%s\"", hovaten); return 0; }
4. strchr()
Hàm strchr() (string character) dùng để tìm kiếm ký tự trong chuỗi.Cú pháp củahàm là:

strchr(str, chr);

, trong đó,chrcó thể là một biến ký tự hoặc một hằng ký tự đều được.

Quy cách hoạt động của hàm này là nó sẽ tìm xem trong chuỗi str có ký tự chr hay không, nếu có thì hàm trả về chuỗibắt đầu từ vị trí đầu tiên tìm thấy ký tựchrcho đến hết chuỗistr, ngược lại thì hàm trả vềNULL.

Chương trình sau đây xác định liệu ký tự 'a' có xuất hiện trong tên hai thành phố hay không.

#include<stdio.h> #include<conio.h> #include<string.h> main() { char str1[15] = "Ha Noi"; char str2[30] = "Thanh pho Ho Chi Minh"; char chr = 'a'; clrscr(); /* nếu khác NULL tức là tìm thấy chr trong str1 */ if(strchr(str1, chr) != NULL){ /* thì in ra ra thông báo có xuất hiện */ printf("\n'%c' co xuat hien trong chuoi \"%s\"\n",chr,str1); } else{ /* nếu không thì thông báo không xuất hiện */ printf("\n'%c' khong xuat hien trong chuoi \"%s\"\n",chr,str1); } /* kiểm tra xem 'a' có nằm trong chuỗi thứ hai không */ if(strchr(str2, chr) != NULL) { printf("\n'%c' xuat hien trong \"%s\"\n",chr,str2); } else{ printf("\n'%c' khong xuat hien trong \"%s\"\n",chr,str2); } return 0; }
5. strstr()
Hàm strstr() (string string) dùng để tìm kiếm chuỗi trong chuỗi.Cú pháp của hàm là:

strstr(Chuỗi1, Chuỗi2)//tìm Chuỗi2 trong Chuỗi1

, trong đó nếu không tìm thấyChuỗi2trongChuỗi1thìhàm trả về giá trị NULL.Ngược lại, hàm sẽ trả về một chuỗi bắt đầu từ vị trí đầu tiên tìm thấyChuỗi2cho đến hếtChuỗi1.Ví dụ:

//khai báo các chuỗi char s1[10] = "abcdefghi", s2[5] = "cde", s3[5] = "cdf"; strstr(s1, s2); //sẽ tìm chuỗi s2 trong chuỗi s1, hàm trả về kết quả là: "cdefghi" strstr(s1, s3); //sẽ tìm chuỗi s3 trong chuỗi s1, hàm trả về kết quả là NULL vì trong chuỗi s1 không có chuỗi "cdf"
6. strcmp()
Hàm strcmp() (string compare) dùng để so sánh hai chuỗi với nhautheo tiêu chí so sánhlàthứ tự ký tự trong bảng mã ASCII.Hàm này thường hay được dùng để sắp xếp các chuỗi theo chiều tăng hoặc giảm theo vần A B C, ví dụ như sắp xếp các tên sinh viên, các tên môn học theo trật tự tăng hoặc giảm.Cú pháp sử dụng hàm này là như sau:

strcmp(s1, s2)

Hàm sẽ trả về một số chính là hiệu của hai ký tự cuối cùng đem so sánh. Cụ thể hàm sẽ trả về giá trị theo các trường hợp sau:

- mộtsốâm (<0) nếu chuỗis1nhỏ hơn chuỗis2.

- số0 (==0) nếu chuỗis1giống hệt chuỗis2.

- một sốdương (>0) nếu chuỗis1lớn hơn chuỗis2.

Quy cách so sánh:

Việc so sánh sẽ bắt đầu từ hai ký tự đầu tiên bên trái của hai chuỗi.Bắt đầu từ bên trái, hàm sẽ lấy từng ký tự của chuỗis2đem so sánh với ký tự ở vị trí tương ứng của chuỗis1.Nếu hai ký tự đem so sánh giống nhau thì sẽ chuyển sang so sánh hai ký tự kế tiếp bên phải.Nếu hai ký tự khác nhau thì lập tức dừng lại và đưa ra kết quả: ký tự nào có thứ tự trong bảng mã ASCII lớn hơn thì chuỗi tương ứng sẽ lớn hơn chuỗi kia.

Chẳng hạn:

Chuỗi "abc" nhỏ hơn chuỗi "abd", vì ký tự 'd' có vị trí lơn hơn ký tự 'c' trong bảng mã ASCII.

Chuỗi "abc" nhỏ hơn chuỗi "abcd".

Chuỗi "An" nhỏ hơn chuỗi "Anh", chuỗi "Anh" nhỏ hơn chuỗi "Binh", ...

Ví dụ:

char s1[5]="Phan", s2[5]="Phi", s3[5]="Phan", s4[7]="Nhuong"; strcmp(s1,s2); //sẽ so sánh s2 với s1, hàm sẽ trả về một số âm (<0) strcmp(s1,s3); //hàm trả về 0 strcmp(s1,s4); //hàm trả về một số dương (>0)
Chương trình sau đây so sánh biếnname1với các biếnname2,name3,name4và hiển thị kết quả của phép so sánh:

#include<stdio.h> #include<conio.h> #include<string.h> main() { char str1[15] = "Ha Noi"; char str2[15] = "Da Nang"; char str3[15] = "Sai Gon"; char str4[15] = "Ha Noi"; int sosanh; sosanh = strcmp(str1,str2); printf("\n\"%s\" so sanh voi \"%s\" thi tra ve %d\n", str1, str2, sosanh); sosanh = strcmp(str1, str3); printf("\n\"%s\" so sanh voi \"%s\" thi tra ve %d\n", str1, str3, sosanh); sosanh = strcmp(str1,str4); printf("\n\"%s\" so sanh voi \"%s\" thi tra ve %d\n", str1, str4, sosanh); return 0; }
7. strrev()
Hàm strrev() (string reverse) dùng để đảo ngược trật tự một chuỗi. Hàm trả về chuỗi đã đượcđổi ngược.Cú pháp của hàm là:

strrev(Chuỗi)

Ví dụ, nếu bạn thực hiện lệnhstrrev("Lap trinh vien");, thì kết quả là chuỗisẽ đảo ngượcthành "neiv hnirt paL".

8. strlwr()
Hàm strlwr() (string lowercase) dùng để chuyểncác ký tự từ 'A' đến 'Z' trong một chuỗi thành in thường, các ký tự khác không thay đổi.

Ví dụ, câu lệnhstrlwr("ABC");sẽ chuyển chuỗi "ABC" thành "abc".

9. strupr()
Hàm strlupr() (string uppercase) dùng để chuyển các ký tự từ 'a' đến 'z' trong một chuỗi thành in HOA, các ký tự khác không thay đổi.

Ví dụ, lệnhstrupr("vietnam");sẽ chuyển chuỗi "vietnam"thành chuỗi"VIETNAM".

10. strncat()
Hàm này dùng để nối n ký tự của chuỗi sau vào sau chuỗi trước. Cú pháp của hàm như sau:

strncat(s1, s2, n)

Theo đó, hàm sẽ nối n ký tự của chuỗi s2 vào sau chuỗi s1.

#include<stdio.h> #include<string.h> main(){ char s1[]="abcd"; char s2[]="1234"; strncat(s1, s2, 2); puts(s1);//Kết quả là: abcd12 return 0; }
11. strncmp()
Hàm này dùng để so sánh n ký tự đầu tiên của hai chuỗi. Cú pháp như sau:

strncmp(s1, s2, n)

Theo đó, hàm sẽ so sánh n ký tự đầu củahai chuỗi s1 và s2 theo quy cách so sánh giống như hàmstrcmp().

#include<stdio.h> #include<string.h> main(){ char s1[]="abcd"; char s2[]="abde"; printf("%d",strncmp(s1, s2, 2)); //So sánh 2 ký tự đầu của 2 chuỗi, sẽ trả về 0 return 0; }
12. strncpy()
strncpy(s1, s2, n)

Hàm này dùng để gán n ký tự đầu tiên của chuỗi s2 cho n ký tự đầu tiên của chuỗi s1.

#include<stdio.h> #include<string.h> main(){ char s1[]="abcd"; char s2[]="1234"; strncpy(s1, s2, 2); //gán 2 ký tự đầu tiên của s2 cho 2 ký tự đầu tiên của s1 puts(s1);//Kết quả của s1: 12cd return 0; }