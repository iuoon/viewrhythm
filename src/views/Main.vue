<template>
  <div class="main">
    <div id="div1" @drop="drop" @dragover="allowDrop" style="{width:90%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;}">
      <img src="../assets/logo.png" draggable="true" @dragstart="drag" id="drag1" :style="elcss" />
    </div>
    <div id="div2" @drop="drop" @dragover="allowDrop"  style="{width:90%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;}"></div>
  </div>
</template>

<script>

export default {
  name: 'Main',
  data () {
    return {
      elcss: {
        position: 'relative', float: 'left', left: '20px', top: '10px'
      },
      elpos: {
        x: 0, y: 0
      }
    }
  },
  methods: {
    allowDrop (e) {
      e.preventDefault()
      this.elpos.x = e.offsetX || e.layerX
      this.elpos.y = e.offsetY || e.layerY
      console.log(this.elpos.x, this.elpos.y)
    },
    drag (e) {
      console.log('00', e)
      e.dataTransfer.setData('Text', e.target.id)
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
