<template>
  <main v-if="!loading">
    <Title :text="title" :dataDate="dataDate"/>
    <Data :stats="stats"/>
    <Countries @getCountry="getCountryData" :countries="countries"/>
    <!-- <div id="main" style="width: 800px; height: 400px;"></div> -->
    <div class="flex content-evenly" v-if="stats.Country">
     <button @click="handleClear" class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600">Clear Current Data</button>
    </div>
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">Downding Data...</div>
    <img :src="loadingImage" class="w-18 m-auto" alt=""/>
  </main>
</template>

<script>
// import echarts from 'echarts'
import Title from '@/components/Title'
import Data from '@/components/Data'
import Countries from '@/components/Countries'
export default {
  name: 'Home',
  components: {
    Title,
    Data,
    Countries
  },
  data () {
    return {
      loading: true,
      title: 'Global Data',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('@/assets/hourglass.gif')
    }
  },
  async created () {
    const data = await this.getData()
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  },
  mounted () {
    // 定义并初始化实例
    // var myChart = echarts.init(document.getElementById('main'))
    // const { data: res } = await fetch('https://api.covid19api.com/')
    // if (res.meta.status !== 200) { return this.$message.error('fail to access data') }
    // myChart.setOption(res.data)
  },
  methods: {
    async getData () {
      try {
        const res = await fetch('https://api.covid19api.com/summary')
        const data = await res.json()
        return data
      } catch (err) {}
    },
    getCountryData (country) {
      this.stats = country
      this.title = country.Country
    },
    async handleClear () {
      this.loading = true
      const data = await this.getData()
      this.title = 'Global Data'
      this.stats = data.Global
      this.loading = false
    }
  }
}
</script>

<style>
</style>
