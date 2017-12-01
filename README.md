<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>五星好评</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul {
            width: 500px;
            list-style: none;
            margin: 30px;
        }
        li {
            font-size: 30px;
            color: red;
            float: left;
        }
    </style>
    <script src="../jQuery/jquery.js"></script>
    <script>
        $(function () {
            var wjx_kx = "☆", wjx_sx = "★";
            // 1.鼠标移动改变星星状态
            $(".list").on("mouseenter", "li", function () {
                // 找到鼠标移动到哪一个星星上面
                $(this)
                    // 把空心换位实心
                    .text(wjx_sx)
                    // 选中前面所有的li标签
                    .prevAll()  // -->此时操作的就是不this
                    // 空心换位实心
                    .text(wjx_sx)
                    // 回到最近的一个"破坏性"操作之前
                    .end()  // -->此时的操作就是this了
                    // 选中后面所有的li标签
                    .nextAll()
                    // 实心换位空心
                    .text(wjx_kx);
            })
            // 2.点击星星做对应的标记
            .on("click", "li", function () {
                $(this).addClass("seleted").siblings().removeClass("seleted");
            })
            // 3.移开鼠标完成评分
            .on("mouseleave", "li", function () {
                // 3.1 找到添加class的标签
                $(".seleted").text(wjx_sx)
                // 3.2 把添加class标签前面的兄弟元素设置为实心
                    .prevAll().text(wjx_sx)
                // 3.3 回到最近的一个"破坏性"操作之前
                    .end()
                // 3.4把添加class标签后面的兄弟元素设置为空心
                    .nextAll().text(wjx_kx);
            })
        });
    </script>
</head>
<body>
<ul class="list">
    <li class="seleted">☆</li>
    <li>☆</li>
    <li>☆</li>
    <li>☆</li>
    <li>☆</li>
</ul>
</body>
</html>
