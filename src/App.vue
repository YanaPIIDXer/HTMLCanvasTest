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
      canvas: null,
      context: null,
      x: 0,
      y: 0,
    }
  },
  mounted: function () {
    this.canvas = this.$refs.canvas
    if (!this.canvas || !this.canvas.getContext) {
      alert('Contextが取得できませんでした')
      return
    }
    this.context = this.canvas.getContext('2d')
    setInterval(this.drawFrame, 60 / 1000)
    document.addEventListener('keydown', this.onKeyDown)
  },
  methods: {
    /**
     * １フレーム分の描画処理
     */
    drawFrame: function () {
      this.context.clearRect(0, 0, this.canvas.width, this.canvas.height)
      this.context.strokeRect(this.x, this.y, 64, 64)
    },
    /**
     * キーが押された
     */
    onKeyDown: function (e) {
      switch (e.key) {
        case 'ArrowLeft':
          this.x -= 10
          break
        case 'ArrowRight':
          this.x += 10
          break
        case 'ArrowUp':
          this.y -= 10
          break
        case 'ArrowDown':
          this.y += 10
          break
      }
    }
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
