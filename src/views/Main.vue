<template>
  <div class="main" style="position: relative;height: 100%">
    <!--<div id="div1" @drop="drop" @dragover="allowDrop" style="position: relative; width:98%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;">-->
      <!--<img src="../assets/logo.png" draggable="true" @dragstart="dragstart" @drag="drag" id="drag1" :style="elc" />-->
    <!--</div>-->
    <!--<div id="div2" @drop="drop" @dragover="allowDrop"  style="position: relative; width:98%; height:200px; margin:10px;padding:10px;border:1px solid #aaaaaa;"></div>-->
    <div id="editor" class="editor" @drop="drop" @dragover="allowDrop">

    </div>
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
      const editor = document.getElementById('editor')
      const p = document.getElementById(e.target.id)
      editor.style.position = 'relative'
      p.style.position = 'relative'
      console.log((e.offsetX - this.elp.offsetX), (e.offsetY - this.elp.offsetY)) //  计算偏移的像素
    },
    drop (e) {
      const that = this
      console.log('22', e)
      const data = e.dataTransfer.getData('Text')
      const el = document.getElementById(data).cloneNode(true) // cloneNode(true)子元素及属性一起拷贝，false不拷贝子元素
      var offset = JSON.parse(localStorage.getItem(el.id))
      el.offsetLeft = offset.left
      el.offsetTop = offset.top
      el.id = that.randNum()
      el.addEventListener('dragstart', function (ev) {
        console.log('110', ev)
        ev.dataTransfer.setData('Text', ev.target.id)
      }, false)
      el.addEventListener('drag', that.drag, true)
      e.target.appendChild(el)
    },
    randNum () {
      var num = ''
      for (var i = 0; i < 6; i++) {
        num += Math.floor(Math.random() * 10)
      }
      return num
    }
  }
}
</script>

<style scoped>
.main{
  float: left;
  width: 82%;
}
.editor{
  height: 100%;
  margin: 3%;
  background-color: #f3f3f3;
}
</style>
