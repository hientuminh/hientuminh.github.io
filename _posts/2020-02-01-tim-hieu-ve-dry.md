---
layout: post
title: DRY - Những điều cần biết
category: Dev
tags: [dev, clean code]
---
## DRY (Don't repeat yourself) là gì
- Đầu tiên code dư thừa không phải là DRY (DON’T REPEAT YOURSELF)
- Định nghĩa về DRY tại https://en.wikipedia.org/wiki/Don%27t_repeat_yourself

## Một vài điểm cần lưu ý với định nghĩa DRY
- Thứ nhất: DRY nói về knowledge không phải là code ( knowledge có thể hiểu là business logic).
- Thứ hai: DRY là nguyên tắc, nguyên lý (giống như SOLID, YAGNI, WET) chứ không phải là quy tắc (rules), do đó không nên áp dụng một cách cứng nhắc.
- Thứ ba (suy ra từ 1): DRY khác với duplicate code.
- Để hiểu hơn về DRY, mọi người có thể đọc 2 link dưới để hiểu cụ thể hơn.
    - https://thevaluable.dev/dry-principle-cost-benefit-example/
    - http://verraes.net/2014/08/dry-is-about-knowledge/
- Về việc phát hiện duplicate code, ta có thể dùng các biện pháp sau:
  - Sử dụng các tool check duplicate code, code smell code
  - Sử dụng search terminal (https://github.com/ggreer/the_silver_searcher)
  - Sử dụng các IDE check duplicate code (chắc là có phí)
- Khi gặp duplicate code, ta có thể cần cân nhắc về việc refactoring sớm. Nó có thể được tái sử dụng hay không (YAGNI) hoặc ghi nhớ một nguyên lý khác là WET.
- Các cách thực hiện để tránh duplicate code:
    - Module helper, utility, mixins
    - Extract method (edited) 