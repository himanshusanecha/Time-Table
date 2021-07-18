<template>
    <div style="overflow-x:auto;">
  <table>
    <tr>
      <th>Course Code</th>
      <th>Course Name</th>
      <th>Link</th>
    </tr>
    <tr v-for="(item, index) in data" :key="index">
      <td>{{ item.Course_Code }}</td>
      <td>{{ item.Course_Name}}</td>
      <td><a :href="item.Link">Link</a></td>
    </tr>
  </table>
</div>

</template>
<script>

export default {
  name: 'ElectiveTable',
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