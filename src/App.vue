<template>
  <Header/>
  <div class="container">
    <router-view/>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
export default {
  data () {
    return {
    }
  },
  components: {
    Header
  }
}
</script>
