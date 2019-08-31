<template>
  <div style=" height: 100%;">
    <Head></Head>
    <div style=" height: 100%;">
      <Left></Left>
      <Main></Main>
    </div>
  </div>
</template>

<script>
import Head from '../components/Head'
import Left from '../components/Left'
import Main from './Main'

export default {
  name: 'Index',
  components: {
    Head: Head,
    Left: Left,
    Main: Main
  }
}
</script>

<style scoped>

</style>
