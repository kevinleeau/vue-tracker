<template>
 <select @change="handleChange" v-model="selected" class="form-select mt-10 block w-full border p-3 rounded">
     <option value="0">Please Select Country</option>
     <option v-for="(country, ID) in countries" :key="ID" :value="country.ID">
         {{country.Country}}
     </option>
 </select>
</template>

<script>
export default {
  name: 'Countries',
  props: ['countries'],
  data () {
    return {
      selected: 0
    }
  },
  methods: {
    handleChange () {
      const currentCountry = this.countries.find((item) => item.ID === this.selected)
      // 函数功能在子组件里实现，但是在home page里渲染
      this.$emit('getCountry', currentCountry)
    }
  }
}

</script>
<style>
</style>
