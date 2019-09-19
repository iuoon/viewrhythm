<template>
    <div class="head">
      <div style="position: relative;left: 50%;height: 100%">
        <div class="head_btn"><Button type="primary" size="large">设  计</Button></div>
        <div class="head_btn"><Button type="primary" size="large">组  件</Button></div>
        <div class="head_btn"><Button type="primary" size="large">我  的</Button></div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Head'
}
</script>

<style scoped>
.head{
  height: 65px;
  border-bottom: 1px solid #57a3f3d9;
}
.head_btn{
  float: left;
  position: relative;
  top: 25%;
  margin-right: 10px;
}
</style>
