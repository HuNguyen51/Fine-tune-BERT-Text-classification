# Fine-tune-BERT-Text-classification là một bài phân loại văn bản báo chí được lấy từ <a href='https://github.com/duyvuleo/VNTC/tree/master/Data/10Topics/Ver1.1'>VNTC</a>
## Giới thiệu
- Các bước xử lý dữ liệu
  - Đầu tiên tải bộ dữ liệu rồi giải nén
  - Đọc dữ liệu
  - Sử dụng thư viện pyvi cho word_segmentation
  - Chuyển dữ liệu từ nhiều file txt thành 1 file csv
- Trong bài này mình sử dụng 2 model đã được train sẵn của vinai
  - một model dùng để tokenize văn bản (dùng để chuyển văn bản thành số)
  - một model dùng để huấn luyện (huấn luyện model dự đoán các nhãn)
## Chi tiết model
- Model train sẵn được sử dụng ở đây là model PhoBERT của vinai <a href='https://huggingface.co/vinai/phobert-base'>vinai/phobert-base</a>
- Các mô hình PhoBERT là mô hình được đào tạo cho tiếng Việt (Pho -> Phở, một món ăn cả Việt Nam)
- Trong bài này chúng ta thấy có sử dụng RobertaForSequenceClassification, thì PhoBERT được đào tạo dựa trên Roberta (theo vinai - PhoBERT pre-training approach is based on RoBERTa which optimizes the BERT pre-training procedure for more robust performance)
- Và RobertaForSequenceClassification là model dùng để cho việc phân loại văn bản với đầu vào là các sequence và đầu ra là một lớp dense với hàm kích hoạt softmax và numclass do mình khởi tạo 
- Chi tiết hơn về PhoBERT của vinai vui lòng xem <a href='https://github.com/VinAIResearch/PhoBERT'>ở đây</a>
## Mô tả cấu trúc thư mục
Train và Test sẽ có cấu trúc chung các file như nhau:  
Train_Full
- label 1 (tên của thư mục cũng là label của các file con trong nó)
  - text file 1 (chứa nội dung của bài báo)
  - text file 2
- label 2
  - text file 1
  - text file 2  
 
Text_Full
- label 1
  - text file 1
  - text file 2
- label 2
  - text file 1
  - text file 2
