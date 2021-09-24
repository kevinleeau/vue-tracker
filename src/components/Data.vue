<template>
 <div class="grid md:grid-cols-2 gap-4">
     <div class="shadow-md bg-blue-100 p-10 text-center rounded">
         <h3 class="text-3xl text-blue-900 font-bold mb-4">Active Cases</h3>
         <div class="text-2xl mb-4">
             <span class="font-bold">New Cases:</span>
             {{commas(stats.NewConfirmed)}}
         </div>
         <div class="text-2xl mb-4">
             <span class="font-bold">Total Cases:</span>
             {{commas(stats.TotalConfirmed)}}
         </div>
     </div>

     <div class="shadow-md bg-blue-300 p-10 text-center rounded">
         <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>
         <div class="text-2xl mb-4">
             <span class="font-bold">New Cases:</span>
             {{commas(stats.NewDeaths)}}
         </div>
         <div class="text-2xl mb-4">
             <span class="font-bold">Total Cases:</span>
             {{commas(stats.TotalDeaths)}}
         </div>
     </div>
 </div>
</template>

<script>
export default {
  name: 'Data',
  props: {
    stats: {
      required: true,
      type: Object
    }
  },
  methods: {
    commas (x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    }
  }
}

</script>
<style>
</style>
