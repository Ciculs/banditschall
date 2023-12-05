# banditschall

## SSH Information

> `Host: bandit.labs.overthewire.org`
> `Port: 2220`

## **Bandit Level 0 → Level 1**

Bằng cách dùng lệnh `ls -a` , ta liệt kê ra được các file có trong folder. Thấy có file readme. Dùng lệnh `cat readme` để đọc file, có flag:

> ![imgs](/imgs/lv0.png)


> Password:  **NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL**

## **Bandit Level 1 → Level 2**

Dùng lệnh `ls -la`, ta thấy file `-` có thể read. Dùng lệnh `cat ./-` để đọc file , có flag

> ![imgs](/imgs/lv1.png)


> Password:  **rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi**

## **Bandit Level 2 → Level 3**

Dùng lệnh `ls -la`, ta thấy file `spaces in this filename` có thể read., `cat space*` để đọc file ( thêm dấu `*` vào cuối file/dir để tự động hoàn thiện tên file nếu không trùng. hoặc có thể cat `filename` để đọc), có flag.

> ![imgs](/imgs/lv2.png)


> Password:  **aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG**

## **Bandit Level 3 → Level 4**:

Dùng lệnh `ls -la`, có folder tên `inhere` , dùng lệnh `cd` để đọc dir , tiếp tục dùng `ls -la` để xem file có trong folder , thấy có 1 file ẩn tên `.hidden` , `cat .hidden` , có flag

> ![imgs](/imgs/lv3.png)


> Password:  **2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe**

## **Bandit Level 4 → Level 5**

Dùng lệnh `ls -la` , `cd inhere`, dùng lệnh `ls -la` , có n file trong đó ,toàn bộ file đều đọc được , đọc qua 1 file thì thấy file không đọc được(không phải plain text). dùng lệnh `file` để xem dạng file bằng cách `file ./*`, thấy có file `-file07` là ASCII , có thể đọc được , `cat ./-file07` , có flag

> ![imgs](/imgs/lv4.png)


> Password:  **lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR**

## **Bandit Level 5 → Level 6**

Dùng lệnh `ls -la` , `cd inhere`, tiếp tục `ls -la` , thấy có rất nhiều folder.

> Dùng lệnh`find -size 1033c`để tìm file theo đề bài. Theo man thì option`-size`để lọc file theo size và c là đơn vị của bytes.
>
> ![imgs](/imgs/manfind.png)


> Thấy file`./maybehere07/.file2`, đọc file bằng lệnh`cat`, có flag.
>
> ![imgs](/imgs/lv5.png)


> Password:  **P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU**

## **Bandit Level 6 → Level 7**

Dùng lệnh `ls -la` , không thấy file nào, đọc mô tả của chall trên overthewire , thấy

> ![imgs](/imgs/otwlv6.png)


Ta dùng lệnh `find / -user bandit7 -group bandit6 -size 33c 2>;/dev/null` để tìm những file thuộc quyền của `user bandit7 `, `group6` và `size = 33 bytes` .Dùng `2>/dev/null` để đưa error vào `/dev/null`. Ta tìm được file `/var/lib/dpkg/info/bandit7.password` phù hợp 3 mô tả đề bài , `cat /var/lib/dpkg/info/bandit7.password` , có flag.

> ![imgs](/imgs/lv6.png)


> Password: **z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S**

## **Bandit Level 7 → Level 8**

## **Bandit Level 8 → Level 9**

## **Bandit Level 9 → Level 10**

## **Bandit Level 10 → Level 11**

## **Bandit Level 11 → Level 12**

## **Bandit Level 12 → Level 13**

## **Bandit Level 13 → Level 14**

## **Bandit Level 14 → Level 15**

## **Bandit Level 15 → Level 16**

## **Bandit Level 16 → Level 17**

## **Bandit Level 17 → Level 18**

## **Bandit Level 18 → Level 19**

## **Bandit Level 19 → Level 20**