<template>
  <div class="form">
    <div class="title">关键词选择表单</div><br />
    <div class="keyword-container">
      <div @mouseenter="e => handleShowTooltip(e, keyword.id)" v-for="keyword in keywordList" :key="keyword.id">
        <el-checkbox>
          <span class="keyword" v-show="!isTooltipList[keyword.id]" >{{ keyword.label }}</span>
          <el-tooltip  v-show="isTooltipList[keyword.id]" class="keyword" :content="keyword.label">
            <span>{{ keyword.label }}</span>
          </el-tooltip>
        </el-checkbox>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
   return {
    keywordList: [
      {id: 'a', label: '黑猫警长'},
      {id: 'b', label: '大鲨鱼吃东西不吐皮阿巴阿巴'},
      {id: 'c', label: '黄土高原上有个大矮敦不知道叫啥'},
      {id: 'd', label: '平凡的世界'},
      {id: 'e', label: '阿凡提骑着毛驴去赶集'},
      {id: 'f', label: '龙马精神最近在演'}
    ],
    isTooltipList: {}
   }
  },
  methods: {
    handleShowTooltip(e, keyword) {
      const { target } = e;
      e.stopPropagation();
      const range = document.createRange();
      range.setStart(target, 0);
      range.setEnd(target, target.childNodes.length);
      // 真实宽度（元素的大小）range.getBoundingClientRect().width，看到的宽度（视口宽度）target.clientWidth
      const rangeWidth = range.getBoundingClientRect().width;
      const isOverflow = Math.floor(rangeWidth) > target.clientWidth;
      this.isTooltipList[keyword] = isOverflow;
      this.isTooltipList = JSON.parse(JSON.stringify(this.isTooltipList));
    }
  }
}
</script>
<style scoped>
.form {
  width: 420px;
  height: 120px;
  border: 1px solid #ccc;
}
.title {
  text-align: center;
}
.keyword-container {
  display: flex;
  flex-wrap: wrap;
}
.keyword {
  display: inline-block;
  width: 140px;
  margin-right: 16px;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  cursor: pointer;
  vertical-align: middle;
}
</style>