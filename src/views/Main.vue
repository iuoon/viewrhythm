<template>
  <div class="main">
    <div id="div1" @drop="drop" @dragover="allowDrop" style="{width:90%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;}">
      <img src="../assets/logo.png" draggable="true" @dragstart="drag" id="drag1" style="position: relative;float:left;left:20px;top:10px;" />
    </div>
    <div id="div2" @drop="drop" @dragover="allowDrop"  style="{width:90%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;}"></div>
  </div>
</template>

<script>

export default {
  name: 'Main',
  methods: {
    allowDrop (ev) {
      console.log('11', ev)
      ev.preventDefault()
    },
    drag (ev) {
      console.log('00', ev)
      ev.dataTransfer.setData('Text', ev.target.id)
    },

    drop (ev) {
      console.log('22', ev)
      ev.preventDefault()
      const data = ev.dataTransfer.getData('Text')
      ev.target.appendChild(document.getElementById(data))
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
