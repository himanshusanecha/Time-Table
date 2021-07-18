<template>
  <div class="topnav" id="myTopnav">
      <a href="#news" :class="{active: (this.isActive>5 || this.isActive < 1) && this.isActive!=8}" @click="setActive(7)">Home</a>
    <a href="#news" :class="{active: this.isActive==1}" @click="setActive(1)">Monday</a>
    <a href="#contact" :class="{active: this.isActive==2}" @click="setActive(2)">Tuesday</a>
    <a href="#about" :class="{active: this.isActive==3}" @click="setActive(3)">Wednesday</a>
    <a href="#about" :class="{active: this.isActive==4}" @click="setActive(4)">Thursday</a>
    <a href="#about" :class="{active: this.isActive==5}" @click="setActive(5)">Friday</a>
    <a href="#about" :class="{active: this.isActive==8}" @click="setActive(8)">Drive Links</a>
    <a href="javascript:void(0);" class="icon" @click="myFunction()">
      <i class="fa fa-bars"></i>
    </a>
  </div>
</template>
<script>
export default {
  name: "Navbar",
  data: function() {
      return {
          isActive: null,
      }
  },
  methods: {
    myFunction() {
      var x = document.getElementById("myTopnav");
      if (x.className === "topnav") {
        x.className += " responsive";
      } else {
        x.className = "topnav";
      }
    },
    TodaysDate() {
        var date = new Date();
        return date.getDay();
    },
    setActive(value) {
        this.isActive = value;
    }
  },
  mounted() {
      this.isActive = this.TodaysDate();
  },
  watch: {
      isActive() {
          this.$emit('active', this.isActive);
      }
  }
};
</script>
<style scoped>
body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

.topnav {
  overflow: hidden;
  background-color: black;
}

.topnav a {
  float: left;
  display: block;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

.topnav a:hover {
  background-color: white;
  color: black;
}

.topnav a.active {
  background-color: white;
  color: black;
}

.topnav .icon {
  display: none;
}

@media screen and (max-width: 600px) {
  .topnav a:not(:first-child) {
    display: none;
  }
  .topnav a.icon {
    float: right;
    display: block;
  }
}

@media screen and (max-width: 600px) {
  .topnav.responsive {
    position: relative;
  }
  .topnav.responsive .icon {
    position: absolute;
    right: 0;
    top: 0;
  }
  .topnav.responsive a {
    float: none;
    display: block;
    text-align: left;
  }
}
</style>