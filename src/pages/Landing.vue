<template>
  <div class="wrapper">
    <doodle :lang="language" class="doodle" />
    <div class="menu-list">
      <div :class="['menu-row', `menu-row-${r+1}`]" v-for="(row, r) in menus" :key="r">
        <a v-for="(menu, i) in row" :key="menu.name"
          :href="menu.name | link({ language })"
          :class="['menu-item', `menu-item-${i+1}`]">
          <text :class="['menu-text', `menu-text-${language}`]">{{i18n(menu.title)}}</text>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
  import Doodle from '../components/Doodle.vue'
  export default {
    components: { Doodle },
    data () {
      return {
        language: 'en',
        menus: [[
          { name: 'guide', title: { en: 'Guide', zh: '教程' } },
          { name: 'examples', title: { en: 'Examples', zh: '实例' } }
        ], [
          { name: 'news', title: { en: 'News', zh: '资讯' } },
          { name: 'about', title: { en: 'About', zh: '关于' } }
        ]]
      }
    }
  }
</script>

<style scoped>
  .doodle {
    width: 750px;
    height: 880px;
  }
  .menu-list {
    flex: 1;
  }
  .menu-row {
    flex: 1;
    flex-direction: row;
    justify-content: center;
    border-top-width: 1px;
    border-top-style: solid;
    border-top-color: #CCC;
  }
  .menu-item {
    flex: 1;
    background-color: #FBFBFB;
    justify-content: center;
    padding-top: 50px;
    padding-bottom: 50px;
  }
  .menu-item:active {
    background-color: #F2F2F2;
  }
  .menu-item-1 {
    border-right-width: 1px;
    border-right-style: solid;
    border-right-color: #CCC;
  }
  .menu-text {
    text-align: center;
    font-size: 52px;
    font-weight: bold;
    color: #8B8B8B;
  }
  .menu-text-zh {
    font-size: 56px;
  }
</style>
