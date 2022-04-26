<template>
  <div class="game" v-on:click="interfaceClicked">
    <span
      class="round"
      ref="round"
      v-on:click.stop="isClicked"
      v-on:click.alt.stop="bonus"
    ></span>
  </div>
</template>

<script>
export default {
  name: "game",
  data: function() {
    return { click: 0 };
  },
  created: function() {
    document.onkeydown = this.start;
  },
  watch: {
    click: function() {
      this.updateRound();
    }
  },
  methods: {
    isClicked: function(event) {
      this.click++;
    },
    bonus: function(event) {
      this.click++;
      console.log("bonus");
      console.log(event);
    },
    interfaceClicked: function(event) {
      this.click++;
    },
    start: function(event) {
      if (event.key === "Enter") {
        console.log("start");
      }
    },
    updateRound: function() {
      let element = this.$refs.round;

      let size = Math.random() * (100 - 10) + 10;
      let top = Math.random() * (60 - 5) + 5;
      let left = Math.random() * (60 - 5) + 5;

      element.style.height = `${size}px`;
      element.style.width = `${size}px`;

      element.style.margin = `${top}% ${left}%`;
    }
  }
};
</script>

<style scoped>
.game {
  width: 100%;
  height: 50%;
  display: block;
  background: rgb(93, 93, 93);
}

.round {
  height: 50px;
  width: 50px;
  background: rgb(225, 225, 225);
  border-radius: 9999px;
  position: absolute;
  margin: 20% 20%;
}
</style>
