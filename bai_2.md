# Bài 2: Git log và Undo commit
## 1. Git log
>Git log để xem lịch sử của các lần commit trước đó.  
Sử dụng lệnh `git log` là sẽ thấy.

```php
    example:
    git log
    commit 565be572f0dc3cc4bf7df463db5a68a75635726f
    Author: anhtuan <nguyenanhtuan23122000@gmail.com>
    Date:   Sat Mar 12 19:54:00 2022 +0700

    c1

    commit 8306dc024251dec2662ebaf586f7b9a8a7235ad5
    Author: anhtuan <nguyenanhtuan23122000@gmail.com>
    Date:   Sat Mar 12 19:52:54 2022 +0700

    c6
```
>Chèn thêm `-p` để hiển thị chi tiết

    commit 565be572f0dc3cc4bf7df463db5a68a75635726f
    Author: anhtuan <nguyenanhtuan23122000@gmail.com>
    Date:   Sat Mar 12 19:54:00 2022 +0700

    c1

    diff --git a/reset.md b/reset.md
    index 64003ba..de63931 100644
    --- a/reset.md
    +++ b/reset.md
    @@ -1,7 +1,3 @@
    tuân c1
    c2
    -c3
    -c4
    -c5
    -c10
    -c11
    +c3
    \ No newline at end of file

>Chèn thêm lệnh để tùy chọn
- --since, --after: Xem các lần commit kể từ ngày nhất định.
- --until: Xem các lần commit trước từ ngày nhất định.
- --author: Xem các lần commit của một người nào đó.
- --grep: Lọc các chuỗi trong log và in ra
>Sử dụng tùy chọn `pretty` để lọc cụ thể hơn

## 2.UNDO COMMIT
>Sử dụng `--amend` để xóa bỏ lần commit trước và cần undo để commit lại
>Sử dụng `git reset HEAD ten_file` để xóa file trong staging area

## 3. Lệnh reset, revert
> Reset sẽ xóa toàn bộ nội dung lịch sử của commit

     $ git log --oneline

    47583d0 (HEAD -> master, tag: exam2) c13
    56b0a24 (tag: exam1-1) c12
    d267a0c (tag: c11.1) c11
    1d2c288 (tag: c10) c10
    7ceeb1c (tag: a1) c9
    f6fb076 c9
    565be57 c1
    8306dc0 c6

    $ git reset --hard 56b0a24

    HEAD is now at 56b0a24 c12

- Khi `reset --hard commit 12` các commit sau đó sẽ bị xóa

>Revert sẽ hoàn lại một sood thay đổi nhưng không xóa đi thứ gì

    $ git revert HEAD

- revert sẽ tạo ra 1 commit mới copy commit trc HEAD

## 4. Thêm tag
>Lightweight Tag đơn thuần là đánh dấu snapshot của commit.

    git tag ten_tag
    git show ten_tag

- Lightweight Tag sẽ tag commit gần nhất

>Annotated Tag có thể đặt tiêu đề cho tag, và khi xem nó sẽ có thông tin về người tag, ngày tag,….

    git tag -a ten_tag -m "ghi chú"
    git show ten_tag

>Thêm tag cho các commit 

    git tag -a ten_tag id_commit -m "ghi chú"

## 5. Thêm tag vào branch

    git checkout -b name_branch name_tag

>Khi đó HEAD sẽ trỏ vào vị trí branch mới với dữ liệu của lần commit gắn tag


