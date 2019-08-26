<template>
  <div style=" height: 100%;">
    <Head></Head>
    <div style=" height: 100%;">
      <Left></Left>
    </div>
  </div>
</template>

<script>
import Head from '../components/Head'
import Left from '../components/Left'
export default {
  name: 'Index',
  components: {
    Head: Head,
    Left: Left
  }
}
</script>

<style scoped>

</style>
