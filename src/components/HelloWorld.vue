<template>
  <div>
    <Navbar @active="Active" />
    <div v-if="this.active >= 1 && this.active <= 5">
      <h1>Section 1</h1>
      <Table class="style" :data="section1" />
      <h1>Section 2</h1>
      <Table class="style" :data="section2" />
      <h1>Elective 1</h1>
      <elective-table :data="electiveData1" class="style"/>
        <h1>Elective 2</h1>
        <elective-table :data="electiveData2"  class="style"/>
    </div>
    <gdrive-table class="style" v-else-if="this.active == 8" />
    <Welcome v-else />
  </div>
</template>

<script>
import GdriveTable from "./GdriveTable.vue";
import Welcome from "./Welcome.vue";
import Navbar from "./Navbar.vue";
import Table from "./TimeTable.vue";
import { getData } from "./../data/data";
import ElectiveTable from './PETable.vue';
import { getData1, getData2 } from './../data/PEdata'
export default {
  components: { Navbar, Table, Welcome, GdriveTable, ElectiveTable },
  name: "HelloWorld",
  data: function () {
    return {
      active: null,
      section1: [],
      section2: [],
      setActive: false,
      electiveData1: getData1(),
      electiveData2: getData2(),
    };
  },
  methods: {
    Active(value) {
      this.active = value;
      this.setActive = true;
    },
  },
  watch: {
    active() {
      if (this.active != null) {
        this.section1 = getData().section1[this.active - 1];
        this.section2 = getData().section2[this.active - 1];
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.style {
  margin: 10%;
}
body {
  background-image: url("./../assets/Codegena.png");
}
h1 {
  color: white;
}
</style>
