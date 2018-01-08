# js timer 定时器 帮助你实现各种定时任务，使用简单
<h3>1、首先创建一个定时器对象 参数mode（1|2） 定时器模式 1代表使用requestAnimationFrame实现 2表示内部采用setTimeout实现，默认模式1<br>var timer = new Timer();</h3>
<section>
    <h3>2、实现一个类似setInterval函数的功能</h3>
<pre><code>var timer = new Timer();
var count = 0;
var id = timer.interval(1000, function() {
    console.log('interval', ++count);
    //计数等于3时，删除该定时任务
    if (count === 3) {
        timer.removeSchedule(id); 
    }
})</code></pre>
</section>
<section>
    <h3>3、实现一个类似setTimeout函数的功能</h3>
<pre><code>var timer = new Timer();
var id = timer.timeout(1000, function() {
    console.log('timeout');
})</code></pre>
</section>
<section>
    <h3>4、使用schedule函数实现一些计划任务</h3>
<pre><code>//每天8, 14, 22点执行一个任务
var timer = new Timer();
var id = timer.schedule({h: [8, 14, 22]}, function() {
    console.log('do');
})</code></pre>

<pre><code>//周六，周日12点执行一个任务
var timer = new Timer();
var id = timer.schedule({h: 12, w: [6, 0]}, function() {
    console.log('do');
})</code></pre>
</section>
<section>
    <h3>5、schedule函数（增加一个任务计划）</h3>
<pre><code>schedule函数有三个参数：rule, fn, once
rule 规则对象 {y:年份, m:月份, d:日, h:时, min:分, s:秒, w:周}
fn 执行的函数
once 执行一次是否自动销毁 默认false否
</code></pre>
</section>
