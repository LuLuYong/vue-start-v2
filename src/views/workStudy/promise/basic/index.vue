<template>
  <div class="container v-promise-basic">
    <p class="v-title">基础代码如下：</p>
    <pre class="line-numbers">
      <code class="language-js">
        new Promise(function(resolve, reject){
          //做一些异步操作
          setTimeout(function(){
            console.log('执行完成');
            resolve('随便什么数据');
          }, 2000);
        });
      </code>
    </pre>
    <p class="v-title">输出：</p>
    <pre>
      <code class="language-js">// 执行完成</code>
    </pre>
    <p class="v-txt">
      在上面的代码中，首先执行了一个异步操作，也就是setTimeout，在2秒后输出'执行完成'，并且调用resolve方法<br/>
      需要注意的是，在上面代码中，只是new了一个promise对象，并没有去调用它而它就执行了，所以在使用promise的时候一般把它封装在一个函数里，然后去运行这个函数，代码如下
    </p>
    <pre class="line-numbers">
      <code class="language-js">
        function runAsync() {
          return new Promise(function(resolve, reject) {
            // 做一些异步操作
            setTimeout(function(){
              console.log('执行完成');
              resolve('随便什么数据');
            }, 2000)
          })
        }
        runAsync();
      </code>
    </pre>
  </div>
</template>

<script>
  import mixin from '@/mixins/prism';
  export default {
    name: 'promise-basic',
    mixins: [mixin]
  }
</script>
