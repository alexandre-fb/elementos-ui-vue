<template>
  <div class="container">
    <TabComponent/>
  </div>
</template>

<script>
// @ is an alias to /src
import TabComponent from '@/components/TabComponent/index.vue'

export default {
  name: 'HomeView',
  components: {
    TabComponent
  }
}
</script>
