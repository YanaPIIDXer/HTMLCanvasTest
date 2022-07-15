<template>
  <div id="app">
    <canvas ref="canvas" width="1024" height="768">
      Canvas非対応
    </canvas>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: function () {
    return {
      context: null,
    }
  },
  mounted: function () {
    const canvas = this.$refs.canvas
    if (!canvas || !canvas.getContext) {
      alert('Contextが取得できませんでした')
      return
    }
    this.context = canvas.getContext('2d')
    this.context.strokeRect(100, 50, 120, 60)
  },
  methods: {
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
