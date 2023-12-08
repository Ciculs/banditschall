# banditschall

## SSH Information

> `Host: bandit.labs.overthewire.org`
>
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

Đề bài hint pass cho lv tiếp theo nằm ở file `/etc/bandit_pass/bandit14` , yêu cầu user bandit14.

- Sau khi ssh bằng usr bandit13 , dùng lệnh `ls` thấy có 1 file `sshkey.private` , là file sshkey cho usr `bandit14`.

- Ta `ssh -i * bandit14@localhost` để login bằng bandit14.

  > ![imgs](/imgs/lv13ssh.png)


- Sau khi ssh vào bandit14 , ta đọc file bằng lệnh `cat /etc/bandit_pass/bandit14` và có password.

  > ![imgs](/imgs/lv13.png)


  Password: **fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq**

## **Bandit Level 14 → Level 15**

Ở bài này , đề bài hint kết nối tới `localhost` ở port `30000` và nhập password hiện tại sẽ ra password cho level tiếp theo.

- Sau 1 hồi phân vân thì em thấy chỉ có netcat khả thi cho trường hợp này.
- Nhập lệnh `nc localhost 30000` , thấy connected ,điền pass của lv hiện tại , ta có pass.

![imgs](/imgs/lv14.png)

Password:**jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt**

## **Bandit Level 15 → Level 16**

Bài này yêu cầu phải kết nối tới `localhost` qua port `30001` bằng ssl.

- Ta dùng `openssl`  để kết nối tới `localhost` bằng lệnh `openssl s_client localhost:30001` (s_client để thiết lập kết nối tới sv).
- Nhập pass của lv này vào , ta có password.

> ![lv15](/imgs/lv15.png)


Password: **JQttfApK4SeyHwDlI9SXGR50qclOAil1**

## **Bandit Level 16 → Level 17**

Đề bài hint cho ta biết password cho lv tiếp theo có thể lấy bằng cách nhập password lv hiện tại vào 1 port ssl của localhost.

- Bước đầu , ta dùng `nmap` để scan port mở của localhost bằng cách `nmap -p 31000-32000 localhost` , có 5 port đang mở.

  > ![imgs](/imgs/lv16nmap.png)


- Ta kết nối tới từng port bằng `openssl` và nhận thấy port `311790` kết nối và trả đúng kết quả là 1 đoạn RSA.

> ![imgs](/imgs/lv16rsa.png)


- Ta tạo 1 folder ở `/tmp` và đi đến folder.
- Dùng lệnh `nano test.private` để tạo 1 file và paste đoạn RSA vào đó.
- Lưu file và làm theo `ssh` tới server như lv13 nhưng file báo `bad permisson`.
- Sau khi đọc trên stackoverflow thì thấy file chỉ cần quyền đọc của user nên ta phải sửa quyền bằng `chmod 600 *`.

> ![imgs](/imgs/stackoverflow.png)


- Sau khi sửa quyền , `ssh` lại , đăng nhập thành công.

> ![imgs](/imgs/lv16chmod.png)


- Tiếp tục cat file password của lv17 tại `/etc/bandit_pass/bandit17`, ta có password lv17.

> ![imgs](/imgs/lv16pass.png)


Password: **VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e**

## **Bandit Level 17 → Level 18**

Đề bài cho 2 file `passwords.old` và `passwords.new`. Pass cho lv tiếp theo ở dòng khác nhau giữa 2 file này.

- Bằng lệnh `diff` , ta có thể dễ dàng nhận ra sự khác nhau giữa 2 file.

> ![imgs](/imgs/lv17.png)


- Có 2 dòng khác nhau , ta thử cả 2 cái bằng cách ssh lv18 , có flag.

> ![imgs](/imgs/lv17correct.png)


Password: **hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg**

## **Bandit Level 18 → Level 19**

Ở level này , sau khi `ssh` vào server , liền bị disconnect.

Mục tiêu: tìm cách để `ssh` mà không bị kick.

Sau khi tìm hiểu ở nhiều nguồn thì em biết có option `-T` để tắt text-terminal.

ÁP DỤNG:

- Dùng lệnh `ssh bandit18@bandit.labs.overthewire.org -p 2220 -T` để kết nối tới server.
- Do có option `-T` nên server không đọc file `.bashrc` (cuối file `bashrc` có `exit` nên bị disconnect) --&gt; không bị disconnect.
- `cat readme` , ta có password.

> ![imgs](/imgs/lv18ssh.png)


Password: **awhqfNnAbc1naukrpqDYcF95h7HoMTrC**

## **Bandit Level 19 → Level 20**

Đề bài có hint về loại file `setuid` , sau khi đọc wiki, ta thấy file đó cấp quyền tạm thời và có quyền exec các lệnh.

- `ssh` với usr `bandit19` , dùng lệnh `ls -la` thấy có file `bandit20-do` và đã có quyền exec.
- `./bandit20-do cat /etc/bandit_pass/bandit20` ta có pass cho lv tiếp theo.

> ![igms](/imgs/lv19.png)


Password: **VxCazJaVykI6W36BkBU0mJTCM8rR95XT**

## **Bandit Level 20 → Level 21**

Ở lv này , server có 1 file `setuid` ở homedir, có chức năng kết nối tới port ta chỉ định. Nếu đọc text ở connection trùng với pass của `bandit20` , cho pass của lv tiếp theo.

- Bước đầu , ta phải host 1 server `netcat` với port tự chọn. Ở đây e chọn `1234`
- Host netcat bằng lệnh `echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | nc -l -p 1234 &` (dấu `&` ở cuối để tiến trình chạy ngầm).
- Dùng file đã cho connect vào server netcat, có password.

> ![imgs](/imgs/LV20.png)


Password: **NvEJF7oVjkddltPSrdKEFOllh9V1IBcq**

## **Bandit Level 21 → Level 22**

Ở đây , bài cho chúng ta biết về 1 `daemon` tên `cron`, thực hiện liên tục những tác vụ lặp đi lặp lại.

- Đầu tiên , `cd /etc/cron.d/` , dùng lệnh `ls` , ta thấy có rất nhiều file của các bandit khác nhưng ở đây, ta chỉ quan tâm đến `bandit22`.
- `cat *bandit22` để đọc file.
- Theo file thì cứ mỗi lần máy `reboot` , file `/usr/bin/cronjob_bandit22.sh` sẽ chạy 1 lần.
- Đọc file `cronjob_bandit22.sh` , ta biết được file này sẽ đọc dữ liệu từ `/etc/bandit_pass/bandit22` và lưu vào `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`.
- Tiếp tục đọc file `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` ,ta có password.

> ![imgs](/imgs/lv21.png)


Password: **WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff**

## **Bandit Level 22 → Level 23**

Tương tự như lv trước. Nhưng code ở lv này phức tạp hơn.

- Cũng như ở lv trước , ta `cd /etc/cron.d/`.
- Đọc file `cronjob_bandit23`, ta thấy tác vụ như ở lv trước.
- Đọc file `/usr/bin/cronjob_bandit23.sh` , ta thấy file sẽ mã hoá `md5` cái gì gì đó nhưng mà hoa mắt quá , em chạy file luôn.
- **NHƯNG** file này đang chạy ở `bandit22` nên ta sẽ không có password chuẩn.

```
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

- Thực thi lệnh `echo I am user bandit23 | md5sum | cut -d ' ' -f 1` , ta có tên folder chứa password cho lv tiếp theo.
- `cat /tmp/8ca319486bfbbc3663ea0fbe81326349` , ta có password.

**GIẢI THÍCH** : Do file này được chạy tự động bởi `cron` sau mỗi lần restart nên sửa `$myname` là ta có tên của file chứa password `bandit23`.

> ![imgs](/imgs/lv22.png)


Password: **QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G**

## **Bandit Level 23 → Level 24**

Ở chall này , theo note thì file sẽ bị xoá sau khi được thực thi.

- Bước đầu, chúng ta `cd /etc/cron.d/`.
- Dùng lệnh `cat *bandit24`.
- Tiếp tục đọc file `bandit24.sh` ta thấy được file này sẽ thực thi file trong folder `/var/spool/$myname/foo`.

> ![igms](/imgs/lv23cron.png)


- Tạo 1 folder trong `tmp` tên `ciculs`.
- Mở folder `cd /tmp/ciculs`
- Tạo file `ciculs.sh` bằng lệnh `nano ciculs.sh`.
- Ta sẽ tạo 1 file `bash` với nội dung như dưới.

```bash
#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/bandit24.txt
```

- Sau khi tạo file xong , dùng lệnh `chmod 777 *` để cấp quyền cho file chạy.
- Di chuyển file đến `/var/spool/bandit24/foo` bằng `cp`.
- Đợi 1 vài phút để `cron` thực hiện tác vụ.
- Sau vài lần check bằng `cat /var/spool/bandit24/foo/ciculs.sh` , thấy file biến mất , ta biết được file đã thực thi.
- Đọc file output , ta có password cho lv tiếp theo.

> ![imgs](/imgs/lv23tieptheo.png)


Password: **VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar**

## **Bandit Level 24 → Level 25**

Bài này yêu cầu chúng ta phải bruteforce vào netcat port 30002 để lấy pass cho chall tiếp theo.

- Đầu tiên , tạo folder con ở `/tmp`.
- Tới folder bằng `cd` và tạo 1 file bash bằng `nano test.sh` với nội dung bên dưới.

```bash
#! /bin/bash 

pass=VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar

for i in {0000..9999}
do
        echo "$pass" "$i"
done
```

> ![imgs](/imgs/lv24dir.png)


- Lưu file và cấp quyền `exec` cho file bằng `chmod +x *`.
- Chạy file kết hợp với `nc localhost 30002` , ta có flag.

> ![imgs](/imgs/lv24pass.png)


Password: **p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d**

## **Bandit Level 25 → Level 26**

Ở đề bài , bài cho ta biết shell của bandit26 không phải `/bin/bash` mà là cái khác.

- `ssh` thử tới server bằng `sshkey` cho sẵn, sau khi kết nối thì liền bị disconnect.
- `cat /etc/passwd` , ta thấy shell của `bandit26` là `/usr/bin/showtext`.
- `cat /usr/bin/showtext`, ta thấy trong file thực thi lệnh `more`.

> ![imgs](/imgs/lv25shell.png)


- Lệnh `more` dùng để đọc nội dung file từng dòng.
- Ta thu nhỏ cửa sổ `ssh` để `more` không hiển thị hết nội dung.
- Ấn `v` để vào `vim`.
- Nhập lệnh `:set shell=/bin/bash`
- Vào lại shell bằng lệnh `:sh`.
- Ta đã `ssh` vào `bandit26` thành công.
- Check lại user bằng `id`. Đúng bandit26
- Lấy password bằng `cat /etc/bandit_pass/bandit26`. Có pass

> ![iMGS](/imgs/lv25.png)


Password: **c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1**

## **Bandit Level 26 → Level 27**

Đề bài không hint gì cả.

- Bằng cách đã sử dụng ở lv trước, `ssh` được vào `bandit26`.
- Dùng lệnh `ls` thấy có file `setuid` của `bandit27`.
- Dùng file `setuid` , ta đọc được password của bandit27 tại `/etc/bandit_pass/bandit27`

> ![imgs](/imgs/lv26.png)


Password: **YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS**

## **Bandit Level 27 → Level 28**

Ở lv này , đề bài yêu cầu `git clone` cơ bản.

- Ta tạo 1 folder ở `tmp` để clone repo về.
- Dùng lệnh `git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo` để clone repo.
- Pass của user = pass của chall hiện tại.
- Sau khi nhập xong , repo đã dc clone về thư mục
- `cd repo` , thấy có 1 file `README`
- `cat *` , có password cho chall tiếp theo.

> !\[imgs\](/imgs/lv27.png

Password: **AVanL161y9rsbcJIsFHuw35rjaOM19nR**

## **Bandit Level 28 → Level 29**

Ở bài này , đề bài y hệt lv trước.

- Tương tự như lv trước , `git clone` repo về.
- `cd repo`, `cat *`

> ![imgs](/imgs/lv28git.png)


- Ta thấy mật khẩu cho `bandit29` đã bị ẩn.
- Dùng `git log` để xem lịch sử `commit`.
- ta thấy có 1 commit có tên `fix info leak`.
- Dùng lệnh `git show 14f754b3ba6531a2b89df6ccae6446e8969a41f3` để xem chi tiết commit.
- Ta thấy có pass của `bandit29`.

> ![imgs](/imgs/lv28.png)

> Password:**tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S**

## **Bandit Level 29 → Level 30**

Vẫn tương tự như ở lv trước.

- Sau khi clone repo về , đọc file README.md , không thấy có gì.
- `git log` cũng không thấy commit nào đáng chú ý.
- Thử đổi sang branch khác xem sao.
- Thử từng cái một.
- `git checkout dev` để chuyển branch `origin` sang `dev`.
- Kiểm tra `log commit` , thấy có 1 commit `add data needed for development`.
- Thử đọc commit , thấy password của lv tiếp theo.

> ![imgs](/imgs/lv29.png)


Password: **xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS**

## **Bandit Level 30 → Level 31**

Như lv trên.

- Sau khi tạo folder và clone repo, đọc file readme , không thấy có gì.
- Check log và branch cũng không có gì.
- Ta sẽ xem thử tới git tagging
- `git tag` , ta thấy có 1 tag tên `secret`.
- `git show secret` , ta có password.

> ![imgs](/imgs/lv30.png)


Password: **OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt**

## **Bandit Level 31 → Level 32**

Cũng như ở lv trước

- Sau khi git clone, đọc file README.md , thấy file yêu cầu phải push lên repo.
- Tạo file `key.txt` theo như yêu cầu của chall.
- `git add -f key.txt` để add file key vào commit.
- `git commit -m"a"` để tạo messsage cho commit.
- `git push` để đẩy commit lên.
- Sau khi push thành công , ta có flag.

> ![imgs](/imgs/lv31.png)


Password: **rmCBvG56y58BXzv98yZGdO7ATVL5dW8y**

## **Bandit Level 32 → Level 33**

Ở chall này , bài yêu cầu phải thoát khỏi cái UPPERSHELL

- Sau khi thử `ls` hay `exit` không được , ta nhập vào `$0` vì nó là bắt đầu của 1 shell.
- Sau khi nhập vào , ta đã ra được shell.
- `whoami` , thấy bandit33\`,