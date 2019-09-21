<template>
    <div>
      <Menu mode="horizontal" theme="light" active-name="1">
        <MenuItem name="1">
          设  计
        </MenuItem>
        <MenuItem name="2">
          市 场
        </MenuItem>
        <MenuItem name="3">
          我 的
        </MenuItem>
      </Menu>
      <!--<div class="head_d">
        <div class="head_btn"><a>设  计</a></div>
        <div class="head_btn"><a>组  件</a></div>
        <div class="head_btn"><a>我  的</a></div>
      </div>-->
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
.head_d{
  position: relative;
  height: 100%;
  width:fit-content;
  width:-moz-fit-content;
  margin: 0 auto;
}
.head_btn{
  float: left;
  position: relative;
  top: 40%;
  margin-right: 10px;
  width:fit-content;
  width:-moz-fit-content;
  font-size: 16px;
}
</style>
