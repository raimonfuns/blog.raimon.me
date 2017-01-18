---
title: 【错误】ApplicationRecord
categories: rails全栈

---

新建model时，默认的代码是长这个样子的

```ruby
class Group < ApplicationRecord
end
```

经常忘记把`ApplicationRecord`改成`ActiveRecord::Base`，同样的错误，犯了2-3次，所以还是把错误记录下来，以免将来再犯。