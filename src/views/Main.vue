<template>
  <div>
    <div id="div1" ondrop="drop(event)" ondragover="allowDrop(event)">
      <img src="../assets/logo.png" draggable="true" ondragstart="drag(event)" id="drag1" />
    </div>
    <div id="div2" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
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
      ev.dataTransfer.setData('Text', ev.target.id)
    },

    drop (ev) {
      ev.preventDefault()
      var data = ev.dataTransfer.getData('Text')
      ev.target.appendChild(document.getElementById(data))
    }
  }
}
</script>

<style scoped>

</style>
