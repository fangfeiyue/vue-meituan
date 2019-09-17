<template>
  <div class="m-menu">
    <dl class="nav" @mouseleave="mouseleave">
      <dt>全部分类</dt>
      <dd v-for="(item, idx) in menu" :key="idx" @mouseenter="mouseenter">
        <i :class="item.type" />{{ item.name }}<span class="arrow" />
      </dd>
    </dl>
    <div v-if="kind" class="detail" @mouseenter="detailEnter" @mouseleave="detailLeave">
      <template v-for="(item, index) in curDetail.child">
        <h4 :key="index">
          {{ item.name }}
        </h4>
        <span v-for="v in item.child" :key="v">{{ v }}</span>
      </template>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      kind: '',
      menu: [{
        type: 'food',
        name: '美食',
        child: [{
          name: '美食',
          child: ['鸡腿', '鸭腿', '米饭']
        }]
      }, {
        type: 'takeout',
        name: '外卖',
        child: [{
          name: '外卖',
          child: ['苹果', '香蕉', '梨']
        }]
      }]
    }
  },
  computed: {
    curDetail () {
      return this.menu.filter(item => item.type === this.kind)[0]
    }
  },
  methods: {
    mouseleave () {
      this.timer = setTimeout(() => {
        this.kind = ''
      }, 150)
    },
    mouseenter (e) {
      this.kind = e.target.querySelector('i').className
    },
    detailEnter () {
      clearTimeout(this.timer)
    },
    detailLeave () {
      this.kind = ''
    }
  }
}
</script>
<style lang="scss">

</style>
