<template>
  <div class="search-panel">
    <el-row class="m-header-searchbar">
      <el-col :span="3" class="left">
        <img src="//s0.meituan.net/bs/fe-web-meituan/fa5f0f0/img/logo.png" alt="美团">
      </el-col>
      <el-col :span="15" class="center">
        <div class="wrapper">
          <el-input v-model="searchContent" placeholder="搜索商家或地点" @focus="onFocus" @blur="onBlur" />
          <button class="el-button el-button--primary">
            <i class="el-icon-search" />
          </button>
          <dl v-if="isHotPlace" class="hotPlace">
            <dt>热门搜索</dt>
            <dt v-for="item in hotPlace" :key="item">
              {{ item }}
            </dt>
          </dl>
          <dl v-if="isSearchList" class="searchList">
            <dd v-for="item in searchList" :key="item">
              {{ item }}
            </dd>
          </dl>
        </div>
        <p class="suggest">
          <a href="#">故宫博物馆</a>
          <a href="#">故宫博物馆</a>
          <a href="#">故宫博物馆</a>
          <a href="#">故宫博物馆</a>
        </p>
        <ul class="nav">
          <li>
            <nuxt-link to="/" class="takeout">
              美团外卖
            </nuxt-link>
          </li>
          <li>
            <nuxt-link to="/" class="movie">
              猫眼电影
            </nuxt-link>
          </li>
          <li>
            <nuxt-link to="/" class="hotel">
              美团酒店
            </nuxt-link>
          </li>
          <li>
            <nuxt-link to="/" class="apartment">
              民宿/公寓
            </nuxt-link>
          </li>
          <li>
            <nuxt-link to="/" class="business">
              商家入驻
            </nuxt-link>
          </li>
        </ul>
      </el-col>
      <el-col :span="6" class="right">
        <ul class="security">
          <li>
            <i class="refund" /><p class="txt">
              随时退
            </p>
          </li>
          <li>
            <i class="single" /><p class="txt">
              不满意免单
            </p>
          </li>
          <li>
            <i class="overdue" /><p class="txt">
              过期退
            </p>
          </li>
        </ul>
      </el-col>
    </el-row>
  </div>
</template>
<script>
export default {
  data () {
    return {
      searchContent: '',
      isFocus: false,
      hotPlace: ['苹果', '香蕉', '梨', '黄瓜'],
      searchList: ['鸡蛋', '鸭蛋', '鸡腿', '蛋糕']
    }
  },
  computed: {
    isHotPlace () {
      return this.isFocus && !this.searchContent
    },
    isSearchList () {
      return this.isFocus && this.searchContent
    }
  },
  methods: {
    onFocus () {
      this.isFocus = true
    },
    onBlur () {
      this.isFocus = false
    }
  }
}
</script>
