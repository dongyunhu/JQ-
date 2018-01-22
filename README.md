___1. 返回顶部按钮___

    你可以利用 animate 和 scrollTop 来实现返回顶部的动画，而不需要使用其他插件。
   <!-- Create an anchor tag -->
    <button class="top">Back to top</button>
    改变 scrollTop 的值可以调整返回距离顶部的距离，而 animate 的第二个参数是执行返回动作需要的时间(单位：毫秒)。
    
   $(document).scroll(function () {
        var top = $(document).scrollTop();
        if ( top > 200) {
            $(".top").fadeIn(200);
        } else {
            $(".top").fadeOut(200);
        }

    });
    // Back to top
    $('a.top').click(function () {
      $(document.body).animate({scrollTop: 0}, 800);
      return false;
    });
    

___2. 预加载图片___

    如果你的页面中使用了很多不可见的图片（如：hover 显示），你可能需要预加载它们：

    $.preloadImages = function () {
      for (var i = 0; i < arguments.length; i++) {
        $('<img>').attr('src', arguments[i]);
      }
    };

    $.preloadImages('img/hover1.png', 'img/hover2.png');


    方法二：
    $.preloadImages = function()
    {
      for(var i = 0; i<arguments.length; i++)
      {
          img = new Image();
          img.src = arguments[i];
      }
    }
    $.preloadImages(
    "path/to/image/1",
    "path/to/image/2",
    "path/to/image/3"
    );

___3. 检查图片是否加载完成___

    有时候你需要确保图片完成加载完成以便执行后面的操作：

    $('img').load(function () {
      console.log('image load successful');
    });
    你可以把 img 替换为其他的 ID 或者 class 来检查指定图片是否加载完成。

___4. 自动修改破损图像___

    如果你碰巧在你的网站上发现了破碎的图像链接，你可以用一个不易被替换的图像来代替它们。添加这个简单的代码可以节省很多麻烦：

    $('img').on('error', function () {
      $(this).prop('src', 'img/broken.png');
    });
    即使你的网站没有破碎的图像链接，添加这段代码也没有任何害处。

    注意： 什么时候使用attr()，什么时候使用prop()？
    1.添加属性名称该属性就会生效应该使用prop();
    prop();只有：selected，checked，autofocus，async，location ( i.e. window.location )，readOnly，multiple
    2.是有true,false两个属性使用prop();
    3.其他则使用attr();

___5. 鼠标悬停(hover)切换 class 属性___

    假如当用户鼠标悬停在一个可点击的元素上时，你希望改变其效果，下面这段代码可以在其悬停在元素上时添加 class 属性，当用户鼠标离开时，则自动取消该 class 属性：

    $('.btn').hover(function () {
      $(this).addClass('hover');
      }, function () {
        $(this).removeClass('hover');
      });
    你只需要添加必要的CSS代码即可。如果你想要更简洁的代码，可以使用 toggleClass 方法：

    $('.btn').hover(function () { 
      $(this).toggleClass('hover'); 
    });
    注：直接使用CSS实现该效果可能是更好的解决方案，但你仍然有必要知道该方法。

  ___6. 禁用 input 字段___

    有时你可能需要禁用表单的 submit 按钮或者某个 input 字段，直到用户执行了某些操作（例如，检查“已阅读条款”复选框）。可以添加 disabled 属性，直到你想启用它时：

    $('input[type="submit"]').prop('disabled', true);
    你要做的就是执行 removeAttr 方法，并把要移除的属性作为参数传入：

    $('input[type="submit"]').removeAttr('disabled');


  ___7. 阻止链接加载___

    有时你不希望链接到某个页面或者重新加载它，你可能希望它来做一些其他事情或者触发一些其他脚本，你可以这么做：

    $('a.no-link').click(function (e) {
      e.preventDefault();
    });

 ___8. 切换 fade/slide___

    fade 和 slide 是我们在 jQuery 中经常使用的动画效果，它们可以使元素显示效果更好。但是如果你希望元素显示时使用第一种效果，而消失时使用第二种效果，则可以这么做：

    // Fade
    $('.btn').click(function () {
      $('.element').fadeToggle('slow');
    });
    // Toggle
    $('.btn').click(function () {
      $('.element').slideToggle('slow');
    });

 ___9. 简单的手风琴效果___

    这是一个实现手风琴效果快速简单的方法：

    // Close all panels
    $('#accordion').find('.content').hide();
    // Accordion
    $('#accordion').find('.accordion-header').click(function () {
      var next = $(this).next();
      next.slideToggle('fast');
      $('.content').not(next).slideUp('fast');
      return false;
    });

___10. 让两个 DIV 高度相同___

    有时你需要让两个 div 高度相同，而不管它们里面的内容多少。可以使用下面的代码片段：

    var $columns = $('.column');
    var height = 0;
    $columns.each(function () {
      if ($(this).height() > height) {
        height = $(this).height();
      }
    });
    $columns.height(height);
    这段代码会循环一组元素，并设置它们的高度为元素中的最大高。

___11. 克隆元素___

    <div>
        <button id="addspp" class="btnadd">button</button>
    </div>
    <script type="text/javascript" src="jquery.js"></script>
    <script type="text/javascript">
        $(function () {
            $('#addspp').on({
                click: function () {
                    var thisperson = $(this).parent().clone();
                    thisperson.children().last().removeClass('btnadd').addClass('btnremo').removeAttr('id');

                    thisperson.children().last().click(function () { 
                      $(this).parent().remove(); 
                    });

                    thisperson.insertBefore($(this).parent().parent().children().last());
                }
            });
        });
    </script>
