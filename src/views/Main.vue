<template>
  <div class="main" style="position: relative;">
    <div id="div1" @drop="drop" @dragover="allowDrop" style="position: relative; width:98%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;">
      <img src="../assets/logo.png" draggable="true" @dragstart="dragstart" @drag="drag" id="drag1" :style="elc" />
    </div>
    <div id="div2" @drop="drop" @dragover="allowDrop"  style="position: relative; width:98%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;"></div>
  </div>
</template>

<script>

export default {
  name: 'Main',
  data () {
    return {
      elc: {
        position: 'relative', float: 'left', left: '20px', top: '10px'
      },
      elp: {
        offsetX: 0,
        offsetY: 0,
        x: 0,
        y: 0
      }
    }
  },
  methods: {
    allowDrop (e) {
      e.preventDefault()
    },
    dragstart (e) {
      console.log('00', e)
      e.dataTransfer.setData('Text', e.target.id)
      const p = document.getElementById(e.target.id)
      this.elp.offsetX = e.offsetX
      this.elp.offsetY = e.offsetY
      console.log(p.offsetLeft, p.offsetTop)
    },
    drag (e) {
      console.log('33')
      const d1 = document.getElementById('div1')
      const p = document.getElementById(e.target.id)
      d1.style.position = 'relative'
      p.style.position = 'relative'
      console.log(p.offsetLeft, p.offsetTop)
      console.log((e.offsetX - this.elp.offsetX), (e.offsetY - this.elp.offsetY)) //  计算偏移的像素
    },
    drop (e) {
      console.log('22', e)
      const data = e.dataTransfer.getData('Text')
      console.log(data)
      e.target.appendChild(document.getElementById(data).cloneNode(true))
    }
  }
}
</script>

<style scoped>
.main{
  float: left;
  width: 82%;
}
</style>
