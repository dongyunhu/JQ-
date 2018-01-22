## 判断 PC 端还是 MOBILE 端 ##
  
       <script type="text/javascript">
        function cssChange(){
            // var link = document.getElementsByTagName('link')[3];
            var link = document.getElementById('aa');
            //PC端应用的样式文件：style_A.css
            alert('当前应用样式文件是：'+link.getAttribute('href'));
            link.setAttribute('href','css/blue.css');
            //Mobile端应用样式文件：style_B.css
            alert('即将应用样式文件是：'+link.getAttribute('href'));
        }
        //懒人建站http://www.51xuediannao.com/
        if    ((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i))) {
           alert('手机端');
            cssChange(); 
        }else{
           alert('pc端')
        }
        </script>
      
### 移动端头部 ###

     //移动端必备

     <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">
