<template>
  <section class="page">
    <h2>curve.catmullRom</h2>
    <p>实现 Catmull Rom 曲线运动。</p>
    <i class="placeholder"></i>
    <h3>使用</h3>
    <p>从 moto.js 里导入 curve。</p>
    <pre><code class="js" v-text="snippets[0]"></code></pre>
    <p>传入至少两个位置点，实现 Catmull Rom 曲线运动。</p>
    <pre><code class="js" v-text="snippets[3]"></code></pre>
    <i class="placeholder"></i>
    <h3>说明</h3>
    <img src="@/static/textures/catmull-rom.gif" alt="">
    <p>curve.catmullRom 函数传入一个参数对象，选项如下：</p>
    <ul>
      <li><i>points:</i><i>包含多个路径点的数组(points.length > 1)</i></li>
      <li><i>speed:</i><i>沿路径移动速度，默认：10</i></li>
      <li><i>loop:</i><i>是否自动闭合路径，默认：false</i></li>
    </ul>
    <p>执行 curve.cubicBezier 函数会返回一个 bezier&lt;object&gt;，包含如下方法：</p>
    <ul>
      <li><i>start:</i><i>开始执行动画</i></li>
      <ul>
        <p>start 接受一个 object 或 function 参数。</p>
        <li><i>{update: (value: number|object) => void, complete: () => void}:</i><i>update: 每帧调用，参数为当前状态值，complete: 动画结束调用</i></li>
        <li><i>update: (value: number|object) => void:</i><i>同上</i></li>
      </ul>
    </ul>
    <p>执行 start 函数会返回一个 action&lt;object&gt;，包含如下方法：</p>
    <ul>
      <li><i>stop:</i>停止动画，stop 后调用 resume 无效</li>
      <li><i>pause:</i>暂停动画，返回 action</li>
      <li><i>resume:</i>恢复动画，返回 action</li>
    </ul>
    <i class="placeholder"></i>
    <h3>演示</h3>
    <p>curve.catmullRom 效果演示。</p>
    <iframe width="100%" height="500" src="//jsfiddle.net/JetLu/c67zqh28/81/embedded/result,js/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>
  </section>
</template>

<script>
  import hljs from 'highlight.js/lib/highlight'
  import javascript from 'highlight.js/lib/languages/javascript'
  import bash from 'highlight.js/lib/languages/bash'
  import html from 'highlight.js/lib/languages/xml'

  hljs.registerLanguage('js', javascript)

  export default {
    data() {
      return {
        snippets: []
      }
    },

    created() {
      import('../snippets/curve.txt').then(res => {
        this.snippets = res.default.split('===').map(item => item.trim())
        this.$nextTick(() => {
          Array.prototype.forEach.call(
            document.querySelectorAll('pre code'),
            item => hljs.highlightBlock(item)
          )
        })
      })
    },

    mounted() {

    }
  }
</script>


<style lang="less" scoped>
  .page {
    color: #5e6d82;
    font-size: .9rem;
    width: 100%;
    padding-bottom: 6rem;

    img {
      margin-bottom: 1rem;
    }

    h2 {
      font-size: 1.8rem;
      color: #333;
      margin: 2rem 0;
      border-bottom: 1px solid #eee;
      padding-bottom: 1rem;

      &:first-child {
        margin-top: 0;
      }
    }

    h3 {
      color: #444;
      font-size: 1rem;
      font-weight: bold;
      margin-bottom: 1rem;
    }

    .placeholder {
      display: block;
      height: 1rem;
    }

    ul {
      list-style-type: disc;
      list-style-position: inside;
      margin: 1rem 0;
      padding-left: 1rem;

      li {
        margin-bottom: .5rem;
        & > i {
          &:first-child {
            font-weight: bold;
            margin-right: 1rem;
          }
        }
      }

      .bold {
        font-weight: bold;
      }
    }
  }
</style>