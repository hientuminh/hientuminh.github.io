---
layout: post
title: Comment - Những điều cần biết
category: Dev
tags: [dev, clean code]
---
## Comments là gì?
- Comments là những dòng, câu rõ nghĩa mà ta muốn tạo ra để ghi chú hoặc giải thích cho một đoạn code. Như vậy comments sẽ hữu ích nếu chúng cung cấp một cách nhìn sâu sắc cho người đọc code những điều mà trong code không thể diễn đạt.
## Đặc điểm
- Điểm yếu của comments đó là dễ bị lỗi thời. Khi ta update code, ta thường quên mất là cần phải update cả comments. Ta cần lưu ý về điểm này nhiều hơn.
- Comments có thể chia làm 3 loại: unncessary, unhelpful, helpful.
## Một số cách để sử dụng comments hiệu quả
- Để hạn chế unncessary comments:
  - Remove comments dư thừa. Lưu ý nếu bạn đang viết code cho public API hoặc library thì cần xem xét vấn đề này kỹ hơn.
  - Thay đổi code để loại bỏ comments
- Cách viết một commet hữu ích
  - **Luôn nhớ:** Comments Tell You Why, Code tells you what.
  - Comments với một ví dụ hữu ích
    ```ruby
    # @param [Array<Hash>] not_created_reports - [{ advertiser_id: 6344, data_type: 'media' }]
    # @return [String] - https://example.com
    def upload_not_created_report_results(not_created_reports)
        yield
    end
    ```
  - Links tới một resources bên ngoài
    ```ruby
    # https://blog.twitter.com/official/ja_jp/topics/product/2017/Cramming-Tweeting-Made-Easier.html
    def invalid_tweet_text?
        yield
    end
```
   - Thêm những actionable comments như TODO, FIXME,
- **NHƯNG TÓM LẠI, ta nên tránh/hạn chế comments khi có thể.**