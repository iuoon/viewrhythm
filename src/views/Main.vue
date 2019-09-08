<template>
  <div class="main">
    <div id="div1" @drop="drop" @dragover="allowDrop" style="{width:90%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;}">
      <img src="../assets/logo.png" draggable="true" @dragstart="dragstart" id="drag1" :style="elc" />
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
      this.elp.x = e.pageX
      this.elp.y = e.pageY
      if (this.elp.x === 0 && this.elp.y === 0) {
        return false
      }
      this.elp.x -= this.elp.offsetX
      this.elp.y -= this.elp.offsetY
      console.log(this.elp.x, this.elp.y)
    },
    dragstart (e) {
      console.log('00', e)
      e.dataTransfer.setData('Text', e.target.id)
      this.elp.offsetX = e.offsetX
      this.elp.offsetY = e.offsetY
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
