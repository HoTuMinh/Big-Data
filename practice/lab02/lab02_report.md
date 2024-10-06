# LAB 02: WORD COUNT PROBLEM 

- input file:
    - nội dung là các từ: "Dear, Bear, River, Car, Car, River, Deer, Car, Bear"
  
- requirement: đếm tần xuất các từ sử dụng MapReduce
  
- idea: tìm các từ duy nhất và đếm số lần xuất hiện các từ này

## I. Sử dụng hàm mẫu WordCount của Hadoop 
1. chuẩn bị file input (dạng .txt)
    - với bài toán word count thì input là một corpus gồm các từ cách nhau bởi dấu cách 
2. tạo thư mục `input` tại hdfs và lưu file data.txt <br/> 
  2.1 tạo thư mục `input` trong hdfs với câu lệnh `hdfs dfs -mkdir /input` <br/>
  2.2 đẩy file `data.txt` vào folder `input` vừa tạo với câu lệnh `hdfs dfs -put "`_where you store data.txt_`" /input` 
4. 

#### II. Lập trình chương trình WordCount bằng Eclipse 
  
#### general steps:
1. **splitting**: chia đầu vào 
2. **mapping**: : với mỗi phần, duyệt từng từ, gán giá trị 1 cho mỗi từ
3. **shorting & shuffling**: nhóm các giá trị cùng một từ
4. **reducing**: tính tổng các giá trị cùng một từ
5. **final result**: tổng hợp kết quả reduce được kết quả cuối cùng

- specific steps:

[reference](https://github.com/demanejar/word-count-hadoop)

