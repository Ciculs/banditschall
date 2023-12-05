# banditschall

## lv0: NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL ( bằng cách dùng lệnh "ls -a" , ta liệt kê ra được các file, , "cat readme" , có flag)

## lv1: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi ( dùng lệnh "ls -la", ta thấy file "-" có thể read , "cat ./- " để đọc file , có flag)

## lv2: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG ( dùng lệnh "ls -la", ta thấy file "spaces in this filename" có thể read , "cat space\*" để đọc file ( thêm dấu \* vào cuối file/dir để tự động hoàn thiện tên file nếu không trùng. hoặc có thể cat "filename" để đọc), có flag)

## lv3: 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe ( dùng lệnh "ls -la", có folder tên "inhere" , dùng lệnh "cd" để đọc dir , tiếp tục dùng "ls -la" để xem file có trong folder , thấy có 1 file ẩn tên ".hidden" , "cat .hidden" , có flag

## lv4: lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR ( dùng lệnh "ls -la" , "cd inhere", dùng lệnh "ls -la" , có n file trong đó ,toàn bộ file đều đọc được , đọc qua 1 file thì thấy file không đọc được(không phải plain text). dùng lệnh "file" để xem dạng file bằng cách "file ./\*", thấy có file -file07 là ASCII , có thể đọc được , "cat ./-file07 , có flag)

## lv5: P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU ( dùng lệnh "ls -la" , "cd inhere", dùng lệnh "file -size 1033c" để tìm file theo đề bài, thấy file "./maybehere07/.file2", đọc file , có flag.

## lv6: