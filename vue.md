# Vue 的基本用法

<div id="main">hello {{ msg }}</div>

<ul>
  <li v-for="i in 10">{{ i }}</li>
</ul>

<script>
  new Vue({
    el: '#main',
    data: { msg: 'Vue' }
  })
</script>
