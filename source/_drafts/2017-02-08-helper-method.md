## helper_method

helper的方法可以在view直接调用，而controller就不行。

那么，怎么让view访问到controller定义的hepler呢？

在controller中用`helper_method`定义属性，就可以在view中使用。

```ruby
class ApplicationController
  helper_method :current_cart
  def current_cart
    cart = Cart.find(session[:cart_id])
    return cart
  end
end
```

## view_context

在controller中不能直接调用helper方法，那应该通过什么方式调用呢？

使用`view_context`。

```ruby
class ProductsController
  def show
    @page_description =  view_context.truncate(@product.desc, :lenght => 50 )
  end
end
```

## 总结

不过还是建议controller和helper之间不要相互调用方法，让view归view，controller归controller，这样就不会太乱。

[http://blog.xdite.net/posts/2014/06/16/helper-method-and-view-context](http://blog.xdite.net/posts/2014/06/16/helper-method-and-view-context)