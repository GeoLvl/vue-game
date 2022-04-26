<template>
  <div class="game">
    <span class="round" v-on:click="isClicked" v-on:click.alt="bonus"></span>
  </div>
</template>

<script>
export default {
  name: "game",
  created: function() {
    document.onkeydown = this.start;
  },
  methods: {
    isClicked: function(event) {
      console.log("click");
    },
    bonus: function(event) {
      console.log("bonus");
      console.log(event);
    },
    start: function(event) {
      if (event.key === "Enter") {
        console.log("start");
      }
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
