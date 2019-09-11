<template>
  <div class="main">
    <div id="div1" @drop="drop" @dragover="allowDrop" style="{position:relative; width:90%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;}">
      <img src="../assets/logo.png" draggable="true" @dragstart="dragstart" @drag="drag" id="drag1" :style="elc" />
    </div>
    <div id="div2" @drop="drop" @dragover="allowDrop"  style="{width:90%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;}"></div>
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
      console.log(p.offsetTop, p.offsetLeft)
    },
    drag (e) {
      console.log('33', e)
      const p = document.getElementById(e.target.id)
      console.log(p.offsetTop, p.offsetLeft)
    },
    drop (e) {
      console.log('22', e)
      e.preventDefault()
      const data = e.dataTransfer.getData('Text')
      e.target.appendChild(document.getElementById(data))
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
