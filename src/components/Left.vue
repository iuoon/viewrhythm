<template>
    <div class="left_1" style="position: relative;">
      <Collapse class="collapse_c_1" simple >
        <Panel name="1" class="panel_c_1">
          史蒂夫·乔布斯
          <p slot="content" ><span draggable="true" @dragstart="dragstart" @drag="drag" id="drag11" :style="elc"><Button>Default1</Button></span> </p>
        </Panel>
        <Panel name="2">
          斯蒂夫·盖瑞·沃兹尼亚克
          <p slot="content"><Button draggable="true" @dragstart="dragstart" @drag="drag" id="drag21" :style="elc" >Default2</Button></p>
        </Panel>
        <Panel name="3">
          乔纳森·伊夫
          <p slot="content">乔纳森·伊夫是一位工业设计师，现任Apple公司设计师兼资深副总裁，英国爵士。他曾参与设计了iPod，iMac，iPhone，iPad等众多苹果产品。除了乔布斯，他是对苹果那些著名的产品最有影响力的人。</p>
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
    allowDrop (e) {
      e.preventDefault()
    },
    dragstart (e) {
      console.log('00', e)
      e.dataTransfer.setData('Text', e.target.id)
    },
    drag (e) {
      console.log('33')
    },
    drop (e) {
      console.log('22', e)
      const data = e.dataTransfer.getData('Text')
      console.log(data)
      e.target.appendChild(document.getElementById(data))
    }
  }
}
</script>

<style scoped>
  .left_1{
    float: left;
    width: 18%;
    border-right: 1px solid #57a3f3d9;
    height: 100%;
  }
  .collapse_c_1{
    float: left;
    width: 90%;
    text-align: left;
    /*box-shadow: 0px 0px 11px 0px #b6b9ff;*/
    margin-top: 20px;
  }

</style>
