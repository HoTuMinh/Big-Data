# CHAPTER 2: PROGRAMMING MODEL MAPREDUCE AND HADOOP 

### Hadoop intro
- **Hadoop là** một công nghệ phân tán và mã nguồn mở được sử dụng phổ biến
để xử lý và lưu trữ khối dữ liệu lớn trên các cụm máy tính phân tán,
được thiết kế để xử lý và lưu trữ dữ liệu lớn một cách hiệu quả
- **được phát triển bởi** Apache Software Foundation, dựa trên công nghệ Google File System và MapReduce
- **đặc điểm** hệ sinh thái Hadoop
  - sử dụng mô hình phân tán để lưu trữ và xử lý dữ liệu trên các máy tính thông thường
  - phân chia dữ liệu thành các khối và lưu chúng
trên nhiều máy tính, giúp tăng khả năng mở rộng, độ tin
cậy và hiệu năng
  -  phân tán dữ liệu trên nhiều nút máy tính và xử lý
nó song song trên các nút, giúp giảm thời gian xử lý và
tăng hiệu suất
- **cấu trúc** hệ sinh thái Hadoop: được xây dựng dựa trên ba phần chính
là **Hadoop Distributes FileSystem (HDFS)**,
**YARN** và **MapReduce**.

### MapReduce model 

- **MapReduce là gì?** 
  - Là mô hình dùng cho xử lý tính toán song song và phân tán
trên hệ thống phân tán

- **MapReduce bao gồm các bước**
1. Phân rã từ nghiệp vụ chính (do người dùng muốn thể
hiện) thành các công việc con để chia từng công việc con
này về các máy tính trong hệ thống thực hiện xử lý một cách
song song
2. Thu thập lại các kết quả
- **Vai trò** trong mô hình MapReduce
  - một máy trong hệ thống là **master**
    - Master chịu trách nhiệm quản lý toàn bộ quá trình thực thi công việc trên hệ thống như
      - tiếp nhận công việc
      - phân rã công việc thành công việc con
      - phân công các công việc con cho các worker 
  - các máy còn lại là **slave**
    - worker chỉ làm nhiệm vụ thực hiện công việc con được giao: thực hiện hàm map hoặc hàm reduce

- **Các bước thực hiện công việc** trên MapReduce
1. chia dữ liệu đầu vào thành các mảnh dữ liệu
2. thực hiện công việc **Map** trên từng mảnh dữ liệu đầu vào $\rightarrow$ Xử lý song song các mảnh dữ liệu trên nhiều máy
tính trong cụm
3. tổng hợp kết quả trung gian (sắp xếp, trộn)
4. Sau khi tất cả công việc Map hoàn thành, thực hiện
công việc Reduce trên từng mảnh dữ liệu trung gian $\rightarrow$ Thực hiện song song các mảnh dữ liệu trung gian trên
nhiều máy tính trong cụm
5. tổng hợp kết quả hàm Reduce để cho kết quả cuối cùng

- Hàm map, reduce
  - MapRedue định nghĩa dữ liệu (cấu trúc và không cấu trúc) dưới dạng
cặp khóa/giá trị (key/value)
    - Map
      - input: một cặp (keyln, valln)
      - output: danh sách các cặp (keyln, valln) trung gian
      - biểu diễn hình thức: map (keyln, valln) $\rightarrow$ list (keyln, valln)
    - Reduce
      - input một cặp (keyInt, list(vallnt))
      - output: danh sách các cặp (keyOut, valOut)
      - biểu diễn hình thức: reduce (keyInt, list(valnt)) $\rightarrow$ list (keyOut, valOut)
  - Map: tiếp nhận mảnh dữ liệu input, rút trích thông tin
cần thiết các từng phần tử (ví dụ: lọc dữ liệu, hoặc trích dữ
liệu) tạo kết quả trung gian
  - Hệ thống thực hiện một bước trung gian để trộn và sắp xếp
lại kết quả
  - Reduce: tổng hợp kết quả trung gian, tính toán để cho
kết quả cuối cùng
  - _Hàm Map và Reduce được xem là phần xử lý quan trọng
nhất trong mô hình MapReduce, do người dùng định nghĩa
tùy theo nhu cầu sử dụng_

### Hadoop MapReduce programming environment 
- [ ] further reading page 20-49

### WordCount problem 
- input file:
  - nội dung là các từ: "Dear, Bear, River, Car, Car, River, Deer, Car, Bear"
  
- requirement: đến tần xuất các từ sử dụng MapReduce
  
- idea: tìm các từ duy nhất và đếm số lần xuất hiện các từ này
  
#### general steps:
1. **splitting**: chia đầu vào 
2. **mapping**: : với mỗi phần, duyệt từng từ, gán giá trị 1 cho mỗi từ
3. **shorting & shuffling**: nhóm các giá trị cùng một từ
4. **reducing**: tính tổng các giá trị cùng một từ
5. **final result**: tổng hợp kết quả reduce được kết quả cuối cùng

- specific steps:

[reference](https://github.com/demanejar/word-count-hadoop)

