<template>
 <div class="text-center">
     <h2 class="text-3xl font-bold">{{text}}</h2>
     <div class="text-2xl mt-4 mb-10"></div>
     {{timestamp}}
 </div>
</template>

<script>
import moment from 'moment'
export default {
  name: 'Title',
  props: {
    text: {
      required: true,
      type: String
    },
    dataDate: {
      required: true,
      type: String
    }
  },
  computed: {
    timestamp () {
      return moment(this.dataDate).format('MMMM Do YYYY, hh:mm:ss a')
    }
  }

}

</script>
<style>
</style>
