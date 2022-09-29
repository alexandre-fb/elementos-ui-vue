<template>
  <div class="container">
    <h1>Tab</h1>

    <div class="tab-container">

      <ul class="tab-header">
        <li class="tab-header__item" :class="activeTabName == tabNames.tab1 ? 'tab-header__item--active' : ''" @click="handleTabClick(tabNames.tab1) ">
          Item 1
        </li>
        <li class="tab-header__item" :class="activeTabName == tabNames.tab2 ? 'tab-header__item--active' : ''" @click="handleTabClick(tabNames.tab2)">
          Item 2
        </li>
      </ul>

      <div class="tab-content">
        <Tab1Component v-if="activeTabName === tabNames.tab1" />
        <Tab2Component v-if="activeTabName === tabNames.tab2" />
      </div>
    </div>
  </div>
</template>

<script>

import Tab1Component from './tabsComponents/Tab1Component.vue'
import Tab2Component from './tabsComponents/Tab2Component.vue'

const tabNames = {
  tab1: 'tab1',
  tab2: 'tab2',
}

export default {
  name: 'TabComponent',
  components: {
    Tab1Component, 
    Tab2Component
  },
  data() {
    return {
      activeTabName: tabNames.tab1,
      tabNames,
    }
  },
  methods: {
    handleTabClick(tabName) {
      this.activeTabName = tabName
      this.currentTabComponent = this.tabsComponents[tabName]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;

  .tab-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    max-width: 1200px;

    .tab-header {
      padding: 0;
      margin: 0;
      display: flex;
      list-style: none;

      .tab-header__item {
        padding: 10px 15px;
        cursor: pointer;

        &:hover {
          background-color: #42b983c9;
          color: #fff;
        }
      }

      .tab-header__item--active {
        background-color: #42b983;
        color: #fff;
      }
    }

    .tab-content {
      width: 100%;
      max-width: 1200px;
      border: 1px solid #42b983;
      background-color: rgb(246, 246, 246);
      border-radius: 5px;
      height: 400px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
}
</style>
