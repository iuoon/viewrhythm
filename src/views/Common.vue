<template>
<div>
 <div @mοusemοve="move1(this)" @mousedown=drag($event) style="position: relative; width:98%; height:200px;width: 200px; margin:10px;padding:10px;border:1px solid #aaaaaa;"></div>
</div>
</template>

<script>
export default {
  name: 'Common',
  methods: {
    move1 (e) {
      console.log(e)
    },
    drag (e) {
      console.log(e)
    }
  }
}
</script>

<style scoped>

</style>
