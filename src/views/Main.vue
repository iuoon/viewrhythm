<template>
  <div>
    <div id="div1" @ondrop="drop(event)" @ondragover="allowDrop(event)" style="{width:90%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;}">
      <img src="../assets/logo.png" draggable="true" @ondragstart="drag(event)" id="drag1" />
    </div>
    <div id="div2" @ondrop="drop(event)" @ondragover="allowDrop(event)"  style="{width:90%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;}"></div>
  </div>
</template>

<script>

export default {
  name: 'Main',
  methods: {
    allowDrop (ev) {
      ev.preventDefault()
    },
    drag (ev) {
      console.log(ev)
      ev.dataTransfer.setData('Text', ev.target.id)
    },

    drop (ev) {
      console.log(ev)
      ev.preventDefault()
      var data = ev.dataTransfer.getData('Text')
      ev.target.appendChild(document.getElementById(data))
    }
  }
}
</script>

<style scoped>

</style>
