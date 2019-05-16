<template>
  <div id="app">
    <div class="desk">
      <div
        class="block"
        :style="{background: item.color}"
        v-for="(item, index) of desk"
        :key="item.id"
        @click="showTurn(index)"
      >
        <img src="./assets/horse.png" class="horse" v-show="item.img">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      desk: []
    };
  },
  mounted: function() {
    var block = {};
    var flag = true;
    for (var i = 0; i < 8; i++) {
      for (var x = 0; x < 8; x++) {
        if (x == 0) {
          flag = !flag;
        }
        block.img = false;
        flag = !flag;

        if (flag === true) {
          block.color = "#da8d35";
        } else {
          block.color = "#312205";
        }
        console.log(block);

        this.desk.push(block);
        block = {};
      }
    }
  },
  methods: {
    showTurn(value) {
      this.desk.length = 0;
      var block = {};
      var flag = true;
      for (var i = 0; i < 8; i++) {
        for (var x = 0; x < 8; x++) {
          if (x == 0) {
            flag = !flag;
          }
          block.img = false;
          flag = !flag;

          if (flag === true) {
            block.color = "#da8d35";
          } else {
            block.color = "#312205";
          }
          console.log(block);

          this.desk.push(block);
          block = {};
        }
      }

      this.desk[value].img = true;

      if (value - 6 >= 0 && value % 8 < 6) {
        this.desk[value - 6].color = "green";
      }
      if (value + 6 < 64 && value % 8 > 1) {
        this.desk[value + 6].color = "green";
      }
      if (value - 10 >= 0 && value % 8 > 1) {
        this.desk[value - 10].color = "green";
      }
      if (value + 10 < 64 && value % 8 < 6) {
        this.desk[value + 10].color = "green";
      }
      if (value - 15 >= 0 && value % 8 < 7) {
        this.desk[value - 15].color = "green";
      }

      if (value + 15 < 64 && value % 8 > 0) {
        this.desk[value + 15].color = "green";
      }

      if (value - 17 >= 0 && value % 8 > 0) {
        this.desk[value - 17].color = "green";
      }

      if (value + 17 < 64 && value % 8 < 7) {
        this.desk[value + 17].color = "green";
      }
    }
  }
};
</script>

<style>
.desk {
  position: absolute;
  height: 322px;
  width: 324px;
}
.block {
  float: left;
  position: relative;
  height: 40px;
  width: 40px;
  border: 1px solid #aa6f2b;
}
.horse {
  height: 40px;
  width: 40px;
}
</style>
