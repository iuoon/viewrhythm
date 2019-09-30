<template>
    <div id="left" class="left" style="position: relative;">
      <Collapse class="collapse" simple value="1">
        <Panel name="1">
          基础组件
          <div slot="content" ><div draggable="true" @dragstart="dragstart" @drag="drag" id="bt_1" style="width: fit-content;width: -moz-fit-content" ><Button style="width: 80px;height: 36px">Default1</Button></div> </div>
        </Panel>
        <Panel name="2">
          更多组件
          <div slot="content"><div draggable="true" @dragstart="dragstart" @drag="drag" id="bt_2" style="width: fit-content;width: -moz-fit-content"><Button>Default2</Button></div> </div>
        </Panel>
        <Panel name="3">
          我的组件
          <div slot="content">
            <Collapse simple >
              <Panel name="1-1">
                iPhone
                <p slot="content">iPhone，是美国苹果公司研发的智能手机，它搭载iOS操作系统。第一代iPhone于2007年1月9日由苹果公司前首席执行官史蒂夫·乔布斯发布，并在2007年6月29日正式发售。</p>
              </Panel>
              <Panel name="1-2">
                iPad
                <p slot="content">iPad是由苹果公司于2010年开始发布的平板电脑系列，定位介于苹果的智能手机iPhone和笔记本电脑产品之间，（屏幕中有4个虚拟程序固定栏）与iPhone布局一样，提供浏览网站、收发电子邮件、观看电子书、播放音频或视频、玩游戏等功能。由英国出生的设计主管乔纳森·伊夫（Jonathan Ive）（有些翻译为 乔纳森·艾维）领导的团队设计的，这个圆滑、超薄的产品反映出了伊夫对德国天才设计师Dieter Rams的崇敬之情。</p>
              </Panel>
            </Collapse>
          </div>
        </Panel>
      </Collapse>
    </div>
</template>

<script>
export default {
  name: 'Left',
  data () {
    return {
      elc: {
        float: 'left', left: '20px', top: '10px'
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
    dragstart (e) {
      console.log('11')
      e.dataTransfer.setData('Text', e.target.id)
      const p = document.getElementById(e.target.id)
      const editor = document.getElementById('editor')
      editor.style.position = 'relative'
      // p.style.position = 'absolute'
      p.style.width = 'fit-content'
      // 计算鼠标点和元素position的偏移量
      var offset = this.getLeftTop(p)
      offset.left = e.pageX - offset.left
      offset.top = e.pageY - offset.top
      console.log(offset.left, offset.top)
      localStorage.setItem(e.target.id, JSON.stringify(offset))
    },
    drag (e) {
      console.log('33-0')
      const editor = document.getElementById('editor')
      const p = document.getElementById(e.target.id)
      p.style.width = 'fit-content'
      editor.style.position = 'relative'
      //  var offset1 = this.getLeftTop(p)
      // var offset2 = this.getLeftTop(editor)
      // var offset = {}
      // offset.left = e.pageX
      // offset.top = e.pageY
      // console.log(offset) //  计算偏移的像素
      // localStorage.setItem(e.target.id, JSON.stringify(offset))
    },
    getLeftTop (obj) {
      var left = obj.offsetLeft
      var top = obj.offsetTop
      var node = obj.offsetParent
      while (node != null) {
        left += node.offsetLeft
        top += node.offsetTop
        node = node.offsetParent
      }
      return { left: left, top: top }
    }
  }
}
</script>

<style scoped>
  .left{
    float: left;
    width: 18%;
    border-right: 1px solid #57a3f3d9;
    height: 100%;
  }
  .collapse{
    float: left;
    width: 90%;
    text-align: left;
    /*box-shadow: 0px 0px 11px 0px #b6b9ff;*/
    margin-top: 20px;
  }

</style>
