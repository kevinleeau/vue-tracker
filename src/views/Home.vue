<template>
  <main v-if="!loading">
    <Title :text="title" :dataDate="dataDate"/>
    <Data :stats="stats"/>
    <Countries :countries="countries"/>
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">Downding Data...</div>
    <img :src="loadingImage" class="w-18 m-auto" alt=""/>
  </main>
</template>

<script>
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
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('@/assets/hourglass.gif')
    }
  },
  async created () {
    const data = await this.getData()
    console.log(data)
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  },
  methods: {
    async getData () {
      try {
        const res = await fetch('https://api.covid19api.com/summary')
        const data = await res.json()
        return data
      } catch (err) {}
    }
  }
}
</script>
