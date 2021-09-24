<template>
 <select @change="handleChange(index)" v-model="selected" class="form-select mt-10 block w-full border p-3 rounded">
     <option value="0">Please Select Country</option>
     <option v-for="(country, index) in countries" :key="index">
         {{country.Country}}
     </option>
 </select>
</template>

<script>
export default {
  name: 'Countries',
  props: {
    countries: {
      type: Object,
      required: true
    }
  },
  data () {
    return {
      selected: 0
    }
  },
  methods: {
    handleChange () {}
  }
}

</script>
<style>
</style>
