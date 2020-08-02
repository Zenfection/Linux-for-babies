# PIPELINES

## 1.Tiêu chuẩn hệ thống `stdin`,`stdout` và `stderr`

Trong Unix, khi chương trình muốn mở một file để đọc hoặc ghi. Nó bắt buộc phải đạt được **"file descriptor"** từ hệ điều hành. Hệ điều hành theo dõi file đó.

Mọi quá trình sẽ tự động giãi mã 3 file descriptor mặc định gọi là **`stdin`** (standard input),**`stdout`** (standard output) và **`stderr`** (standard error). Ba file descriptor đó gọi là chung là **"standard steams"**.

Trong lịch sử, **"stardand input"**-**`stdin`** nghĩa là bàn phím vật lý và hai đầu ra nghĩa là màn hình, trong unix điều này nó trừu tượng và rất khó hiểu. Do đó, đọc chương trình từ **`stdin`** không biết được liệu những gì nhập vào có phải do con người hay không, với chương trình khác, network hoặc các nguồn khác. Tương tự như vậy, chương trình ghi bằng **`stdout`** không biết liệu xuất thứ được hiển thị trên màn hình.

Những thứ khó hiểu trên nói cho nó dễ hiểu là: **`stdin`** là những thứ gì nhập vào chương trình, còn **`stdout`** là những thứ xuất ra màn hình.

## 2. Những điều cơ bản của Pipe Operator

Trong Unix, mọi quá trình đều có ba luồng tiêu chuẩn: **`stdin`**,**`stdout`**, và **`stderr`**. Bởi mặc định bất kỳ quá trình ghi **`stdout`** sẽ xuất hiện dưới dạng văn bản **console**.

Tuy nhiên, chúng ta có thể làm cho nó để một quá trình **`stdout`** được đính kèm một quá trình **`stdin`** để sản xuất ra **"pipeline"**.

Để làm điều đó, chúng ta sử dụng dấu **`|`**. Nhìn ví dụ sau đây:

```shell
$ ps ax | grep mysql
2922 ?       S      0:00
     /bin/sh /usr/bin/mysqld_safe
3164 ?       SL   204:21
     /usr/sbin/mysqld
$
```

Lệnh **`px ax`** ghi một danh sách các tiến trình hiện đang chạy đến **`stdout`**. Lệnh **`grep mysql`** đọc tử **`stdin`** và ghi tất cả những dòng nhập chứa **"mysql"** đến **`stdout`**.

Cùng với nó, chúng ta có thể nhận "pipeline" duy nhất liệt kê các tiến trình hiện đang chạy với tên chứa **"mysql"**.Điều quan trọng là **`ps`** và **`grep`** cả 2 liên quan với nhau trong quá trình **`stdin`** và **`stdout`**. Hệ điều hành gộp 2 quá trình này lại với nhau bằng dấu **`|`**








