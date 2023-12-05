# banditschall

## SSH Information

> `Host: bandit.labs.overthewire.org`
> `Port: 2220`

## **Bandit Level 0 → Level 1**

Bằng cách dùng lệnh `ls -a` , ta liệt kê ra được các file có trong folder. Thấy có file readme. Dùng lệnh `cat readme` để đọc file, có flag:

> ![imgs](/imgs/lv0.png)


> NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

## **Bandit Level 1 → Level 2**

Dùng lệnh `ls -la`, ta thấy file `-` có thể read. Dùng lệnh `cat ./-` để đọc file , có flag

> ![imgs](/imgs/lv1.png)


> rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

## **Bandit Level 2 → Level 3**

Dùng lệnh `ls -la`, ta thấy file `spaces in this filename` có thể read., `cat space*` để đọc file ( thêm dấu `*` vào cuối file/dir để tự động hoàn thiện tên file nếu không trùng. hoặc có thể cat `filename` để đọc), có flag.

> ![imgs](/imgs/lv2.png)


> aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

## **Bandit Level 3 → Level 4**:

Dùng lệnh `ls -la`, có folder tên `inhere` , dùng lệnh `cd` để đọc dir , tiếp tục dùng `ls -la` để xem file có trong folder , thấy có 1 file ẩn tên `.hidden` , `cat .hidden` , có flag

> ![imgs](/imgs/lv3)


> 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

## **Bandit Level 4 → Level 5**

lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR ( dùng lệnh "ls -la" , "cd inhere", dùng lệnh "ls -la" , có n file trong đó ,toàn bộ file đều đọc được , đọc qua 1 file thì thấy file không đọc được(không phải plain text). dùng lệnh "file" để xem dạng file bằng cách "file ./\*", thấy có file -file07 là ASCII , có thể đọc được , "cat ./-file07 , có flag)

## **Bandit Level 5 → Level 6**

P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU ( dùng lệnh "ls -la" , "cd inhere", dùng lệnh "file -size 1033c" để tìm file theo đề bài, thấy file "./maybehere07/.file2", đọc file , có flag.

## **Bandit Level 6 → Level 7**

z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S ( dùng lệnh "ls -la" , không thấy file nào, đọc mô tả của chall trên overthewire , thấy (img). Ta dùng lệnh "find / -user bandit7 -group bandit6 -size 33c 2&gt;/dev/null" để tìm những file thuộc quyền của user bandit7 , group6 và size = 33bytes. 2&gt;/dev/null để đưa error vào /dev/null. Ta tìm được file "/var/lib/dpkg/info/bandit7.password" phù hợp 3 điều kiện đề bài , "cat /var/lib/dpkg/info/bandit7.password" , có flag.

## lv7: