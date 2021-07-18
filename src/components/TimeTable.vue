<template>
    <div style="overflow-x:auto;">
  <table>
    <tr>
      <th>Time</th>
      <th>Course Code</th>
      <th>Link</th>
    </tr>
    <tr v-for="(item, index) in data" :key="index">
      <td>{{ item.time }}</td>
      <td>{{ item.Course_Code}}</td>
      <td v-if="item.Link==null && item.Link1==null"></td>
      <td v-else-if="!item.variation"><a :href="item.Link">Link</a></td>
      <td v-else><a :href="item.Link1">CS305</a> / <a :href="item.Link2">IT301</a></td>
    </tr>
  </table>
</div>

</template>
<script>

export default {
  name: 'TimeTable',
  props: {
    data: []
  },
  mounted() {
    console.log(this.data);
  }
}
</script>

<style scoped>
table {
  border-collapse: collapse;
  border-spacing: 0;
  width: 100%;
  border: 1px solid #ddd;
}

th, td {
  text-align: left;
  padding: 8px;
}

tr {background-color: #f2f2f2}
</style>