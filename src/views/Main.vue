<template>
  <draggable>
    <transition-group>
      <div :key="1">
        <span>1111</span>
      </div>
      <div :key="2">
        <span>2222</span>
      </div>
    </transition-group>
  </draggable>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  name: 'Main',
  components: {
    draggable
  }
}
</script>

<style scoped>

</style>
