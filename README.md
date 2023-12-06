# banditschall

## SSH Information

> `Host: bandit.labs.overthewire.org`
> `Port: 2220`

## **Bandit Level 0 → Level 1**

- Bằng cách dùng lệnh `ls -a` , ta liệt kê ra được các file có trong folder.
- Thấy có file readme.
- Dùng lệnh `cat readme` để đọc file, có flag:

> ![imgs](/imgs/lv0.png)


> Password:  **NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL**

## **Bandit Level 1 → Level 2**

- Dùng lệnh `ls -la`, ta thấy file `-` có thể read.

- Dùng lệnh `cat ./-` để đọc file , có flag

> ![imgs](/imgs/lv1.png)


> Password:  **rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi**

## **Bandit Level 2 → Level 3**

- Dùng lệnh `ls -la`, ta thấy file `spaces in this filename` có thể read.
- `cat space*` để đọc file ( thêm dấu `*` vào cuối file/dir để tự động hoàn thiện tên file nếu không trùng. hoặc có thể cat `filename` để đọc). Có flag.

> ![imgs](/imgs/lv2.png)


> Password:  **aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG**

## **Bandit Level 3 → Level 4**:

- Dùng lệnh `ls -la`, có folder tên `inhere` ,
- Dùng lệnh `cd` để đọc dir .
- Tiếp tục dùng `ls -la` để xem file có trong folder , thấy có 1 file ẩn tên `.hidden`.
- `cat .hidden` , có flag

> ![imgs](/imgs/lv3.png)


> Password:  **2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe**

## **Bandit Level 4 → Level 5**

- Dùng lệnh `ls -la` .
- Tiếp tục `cd inhere`
- Dùng lệnh `ls -la` , có n file trong đó ,toàn bộ file đều đọc được , đọc qua 1 file thì thấy file không đọc được(không phải plain text).
- Dùng lệnh `file` để xem dạng file bằng cách `file ./*`, thấy có file `-file07` là ASCII , có thể đọc được .
- `cat ./-file07` , có flag

> ![imgs](/imgs/lv4.png)


> Password:  **lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR**

## **Bandit Level 5 → Level 6**

- Dùng lệnh `ls -la`
- `cd inhere`
- Tiếp tục `ls -la` , thấy có rất nhiều folder.

> Dùng lệnh`find -size 1033c `để tìm file theo đề bài. Theo man thì option`-size`để lọc file theo size và c là đơn vị của bytes.
>
> ![imgs](/imgs/manfind.png)


> Thấy file`./maybehere07/.file2`, đọc file bằng lệnh`cat`, có flag.
>
> ![imgs](/imgs/lv5.png)


> Password:  **P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU**

## **Bandit Level 6 → Level 7**

- Dùng lệnh `ls -la` , không thấy file nào, đọc mô tả của chall trên overthewire , thấy

> ![imgs](/imgs/otwlv6.png)


- Ta dùng lệnh `find / -user bandit7 -group bandit6 -size 33c 2>;/dev/null` để tìm những file thuộc quyền của `user bandit7 `, `group6` và `size = 33 bytes` .
- Dùng `2>/dev/null` để đưa error vào `/dev/null`. Ta tìm được file `/var/lib/dpkg/info/bandit7.password` phù hợp 3 mô tả đề bài.
- `cat /var/lib/dpkg/info/bandit7.password` , có flag.

> ![imgs](/imgs/lv6.png)


> Password: **z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S**

## **Bandit Level 7 → Level 8**

- Bằng lệnh `ls` , có thể thấy có đúng duy nhất 1 file `data.txt` . Theo như đề bài , ta biết password nằm cạnh cụm `millionth`.

> ![imgs](/imgs/debai7.png)


> Ta dùng lệnh `grep` để tìm cụm từ có nội dung `millionth` và kết quả hiện ra là password cần tìm.
>
> ![imgs](/imgs/lv7.png)


Password: **TESKZC0XvTetK0S9xNwm25STk5iWrBvP**

## **Bandit Level 8 → Level 9**

- Sau khi `ls` thì ta thấy có duy nhất 1 file.
- `cat` file ra thì thấy có rất nhiều giá trị
- Theo đề bài , cần tìm ra 1 giá trị không bị trùng và duy nhất.
- Bước đầu , ta dùng lệnh `sort` để sắp xếp lại các giá trị trong file.
- Tiếp theo dùng `uniq -u` để lọc ra giá trị duy nhất của file(option `-u` dùng lể lọc ra giá trị unique (là duy nhất)).
- Sau khi lọc xong giá trị , ta có duy nhất 1 dòng, đó là password cần tìm.

> ![imgs](/imgs/lv8.png)


Password: **EN632PlfYiZbn3PhVK3XOGSlNInNE00t**

## **Bandit Level 9 → Level 10**

- Đề bài nói password nằm trong file `data.txt` , là kí tự đọc được và đứng đằng sau vài dấu `=`.
- Đầu tiền , `ls` ra thì có duy nhất 1 file `data.txt` .
- Dùng lệnh `file` để xem dạng file của file này thì thấy là 1 file data(không thể đọc bằng `cat`).
- Ta dùng `strings` để đọc những file data như này và kết hợp với `grep` để tìm ra những dấu `=`.
- Lọc ra được vài kết quả thì với ta , cái dài nhất có vẻ là password, sau khi đăng nhập thử, xác định nó là password.

> ![imgs](/imgs/lv9.png)


Password: **G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s**

## **Bandit Level 10 → Level 11**

Theo đề bài thì password dc enc base64. Sau khi `ls` , thấy có duy nhất 1 file `data.txt`, `cat` ra thì có được 1 chuỗi base64 đã enc , dùng cyberchef giải base64 , có được password.

> ![imgs](/imgs/lv10.png)


> ![imgs](/imgs/xaibochep.png)


Password: **6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM**

## **Bandit Level 11 → Level 12**

- Ở lv này , cách làm tương tự như lv10 nhưng thay vì base64, chall dùng ROT13.

> ![imgs](/imgs/lv11.png)


> ![imgs](/imgs/xaibochep11.png)


Password: **JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv**

## **Bandit Level 12 → Level 13**

- Sau 1 hồi tìm hiểu thì em biết `xxd` có thể tạo và reverse hexdump.
- Bước đầu , ta dùng tạo folder trong `/tmp` theo như đề bài và chuyển file `data.txt` qua đó cho tiện thực hiện.
- Sau đó , dùng lệnh `xxd -r * > 1` để reverse file `data` và xuất thành file `1`.
- Dùng lệnh `file 1` để xem `1` là loại file gì.

> Đây là 1 file`gzip`
>
> ![imgs](/imgs/bandit12/1.png)


- Ta đổi đuôi file thành `gz` để giải nén bằng lệnh `mv 1 1.gz`
- Và giải nén file bằng `gzip -d 1.gz` (option -d để xoá file gzip sau khi đã giải nén).
- Ta được file `1`
- Dùng lệnh `file` để xem dạng file `1` , ta thấy file `1` là 1 file `bzip2`.

> Đây là 1 file`bzip2`
>
> ![imgs](/imgs/bandit12/2.png)


- Tiếp tục đổi đuôi file sang `bz2` bằng lệnh `mv 1 1.bz2`
- Dùng `bzip2 -d 1.bz2` để giải nén , có file `1`
- Dùng `file` để xác định file `1` , thấy đó là 1 file `gzip`

> ![imgs](/imgs/bandit12/3.png)


- Tiếp tục đổi đuôi bằng `mv 1 1.gz`
- Giải nén bằng `gzip`, ta tiếp tục có file `1`.
- Dùng `file` để xác định, đây là 1 file `tar`

> ![imgs](/imgs/bandit12/4.png)


- Giải nén file bằng `tar -xf` , có ra 1 file `data5.bin`
- Dùng `file` để xác định kiểu file, thấy là 1 file `tar` , tiếp tục giải nén.
- Giải nén ra được file `data6.bin` , xác định bằng `file` , đây là 1 file `bzip2`

> ![imgs](/imgs/bandit12/5.png)


- Cứ tiếp tục giải nén , ta có file `data8` , là 1 file `ASCII`.
- `cat data8` , ta có password.

> ![?](/imgs/bandit12/6.png)


Password: **wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw**

## **Bandit Level 13 → Level 14**

Đề bài yêu cầu

## **Bandit Level 14 → Level 15**

## **Bandit Level 15 → Level 16**

## **Bandit Level 16 → Level 17**

## **Bandit Level 17 → Level 18**

## **Bandit Level 18 → Level 19**

## **Bandit Level 19 → Level 20**