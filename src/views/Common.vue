<template>
<div>
 <div style="position: relative; width:98%; height:200px;width: 200px; margin:10px;padding:10px;border:1px solid #aaaaaa;"></div>
  <img src="../assets/logo.png" id="drag1" :style="elc"  @mοusemοve="move1(this)" @mousedown=drag($event) />
</div>

</template>

<script>
export default {
  name: 'Common',
  data () {
    return {
      elc: {
        position: 'relative', float: 'left', left: '20px', top: '10px'
      }
    }
  },
  mounted () {
    window.addEventListener('click', this.handleClick)
    // window.addEventListener('mousemove', this.handleMousemove)
  },
  methods: {
    move1 (e) {
      console.log(e)
    },
    drag (e) {
      console.log(e)
    },
    handleClick (e) {
      console.log(e)
    }
    // handleMousemove (e) {
    //   console.log(e)
    // }
  },
  destroyed () {
    window.removeEventListener('click', this.handleClick)
    // window.removeEventListener('mousemove', this.handleMousemove)
  }
}
</script>

<style scoped>

</style>
