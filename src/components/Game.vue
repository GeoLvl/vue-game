<template>
  <div class="game" @click="clickOnInterface">
    <span
      class="round"
      :style="roundStyle"
      :class="{ bonus: bonusActivated, badColor: badColorActivated }"
      @click.stop="clickOnRound"
      @click.alt.stop="bonus"
    ></span>
  </div>
</template>

<script>
export default {
  name: "game",
  data: function() {
    return {
      click: 0,
      roundStyle: {
        height: "50px",
        width: "50px",
        margin: "20% 20%"
      },
      bonusActivated: false,
      badColorActivated: false
    };
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
    clickOnRound: function(event) {
      this.click++;
    },
    bonus: function(event) {
      if (this.bonusActivated) {
        console.log("PERFECT");
      } else {
        console.log("Wtf man !");
      }
    },
    clickOnInterface: function(event) {
      this.click++;
      console.log("INTERFACE");
    },
    start: function(event) {
      if (event.key === "Enter") {
        console.log("START");
      }
    },
    updateRound: function() {
      let size = Math.random() * (100 - 10) + 10;
      let top = Math.random() * (60 - 5) + 5;
      let left = Math.random() * (60 - 5) + 5;

      this.badColorActivated = size < 20;
      this.bonusActivated = size > 80;

      this.roundStyle.height = this.roundStyle.width = `${size}px`;
      this.roundStyle.margin = `${top}% ${left}%`;
    }
  }
};
</script>

<style scoped>
.game {
  width: 100%;
  height: 100%;
  display: block;
  background: #6d6b6b;
}

.round {
  background: aliceblue;
  border-radius: 9999px;
  position: absolute;
}

.bonus {
  background: indianred;
}

.badColor {
  background: #7d7d7d;
}
</style>
