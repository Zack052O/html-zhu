# 搜🐖输入法！
本项目为zack独立原创制作成果，为仿sg输入法制作
代码部分：HTML主页、IMG、JS、CS

## 项目结构
本项目包括以下主要部分：
- HTML：构成网页的骨架。
- IMG：网页中使用的所有图片资源。
- JS：提供网页的交互逻辑。
- CSS：定义网页的样式和布局。

**效果如下：**
![link](https://github.com/Zack052O/html-zhu/blob/main/%E9%A6%96%E9%A1%B5%E6%95%88%E6%9E%9C%E5%9B%BE.png)
**第二页效果**
![2](https://github.com/Zack052O/html-zhu/blob/main/%E7%AC%AC%E4%BA%8C%E9%A1%B5%E6%95%88%E6%9E%9C%E5%9B%BE.png)
**第三页效果**
![3](https://github.com/Zack052O/html-zhu/blob/main/footer%E6%95%88%E6%9E%9C%E5%9B%BE.png)



## 详细代码解释
### 1、HTML 结构
本项目的 HTML 结构分为三个主要部分，每个部分占据屏幕的100%：
***
**首页**
```
   <div class="full-screen-box">
    <header style="box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.1);">
        <!-- 头部内容 -->
    </header>
    <!-- 主页轮播 -->
    <div class="carousel-indicators">
        <!-- 轮播指示器 -->
    </div>
    <!-- 七大下载盒子 -->
    <div class="content-boxes">
        <!-- 下载内容盒子 -->
    </div>
</div>

```
**第二页**
```
<section class="industry-solutions">
    <div class="solutions-title">为不同行业定制的多场景输入方案</div>
    <nav class="solutions-nav">
        <!-- 导航链接 -->
        <a class="nav-link" data-target="office" href="#">智能办公</a>
        <!-- 更多导航链接 -->
        <!-- 内容盒子 -->
        <div class="solutions-content">
            <!-- 解决方案内容 -->
        </div>
    </nav>
    <div style="padding: 20px; margin-top: 30vh;">
        <div>
            <h2>更多优秀案例</h2>
            <!-- 案例内容 -->
        </div>
    </div>
</section>


  ```
  **第三页**
  ```
  <footer>
    <!-- 页脚内容 -->
  </footer>

   ```
  ### 2、JavaScript 逻辑

  **轮播图控制**
  ***
 - 功能说明：控制轮播图指示器的状态，以反映当前显示的幻灯片。
 - 实现方法：changeSlide(slideNumber) 函数，根据传入的 slideNumber 参数激活相应的指示器。
  ```
 // 轮播图
 function changeSlide(slideNumber) {
    const indicators = document.querySelectorAll('.carousel-indicator');
    indicators.forEach((indicator, index) => {
        indicator.classList.toggle('active', index === slideNumber);
    });
}

document.addEventListener('DOMContentLoaded', () => {
    changeSlide(0); // 页面加载时激活第一个指示器
    document.querySelectorAll('.carousel-indicator').forEach((indicator, index) => {
        indicator.addEventListener('click', () => {
            changeSlide(index); // 点击指示器时切换幻灯片
        });
    });
});

  ```
  **第二部分：导航链接内容显示**
  ***
  - 功能说明：根据点击的导航链接显示相应的内容盒子，隐藏其他内容。
  - 实现方法：在页面加载完成后，添加事件监听器，点击导航链接时切换激活状态。
```
document.addEventListener('DOMContentLoaded', function () {
    var navLinks = document.querySelectorAll('.nav-link');
    var contentPanes = document.querySelectorAll('.content-pane');

    navLinks.forEach(function (link) {
        link.addEventListener('click', function (event) {
            event.preventDefault();
            navLinks.forEach(lnk => lnk.classList.remove('active'));
            contentPanes.forEach(pane => pane.classList.remove('active'));

            this.classList.add('active');
            var targetId = this.getAttribute('data-target');
            var targetPane = document.getElementById(targetId);
            if (targetPane) {
                targetPane.classList.add('active');
            }
        });
    });

    // 页面加载时自动激活第一个导航链接
    if (navLinks.length > 0) {
        navLinks[0].click();
    }
});

```
