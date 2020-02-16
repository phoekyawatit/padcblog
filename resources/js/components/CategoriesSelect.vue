<template>
  <form-group label="Caregory : ">
    <select name="category_id">
      <option v-for="category in categories" :key="category.id" :value="category.id">{{category.name}}</option>
    </select>
  </form-group>
</template>
<script>
export default {
  props : ['token'],
  data() {
    return {
      categories: []
    };
  },
  created() {
    const token = this.token;
    const url = `/api/web/v1/category`
    axios.get(url).then(response => {
      this.categories = response.data;
    });
  }
};
</script>