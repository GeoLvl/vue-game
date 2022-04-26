<template>
  <div>
    <span v-hide>id player : {{ greetings }}</span>
    <form v-hide v-on:submit.prevent="setPlayer">
      <input name="player" placeholder="Entrez votre pseudo" v-border:red />
      <button v-border:green>Jouer</button>
    </form>
  </div>
</template>

<script>
// import { directive } from "vue/types/umd";
export default {
  name: "player",
  data: function() {
    return {
      player: "",
      greetings: ""
    };
  },
  updated: function() {
    // this.player = "";
    // this.playerClass = this.player ? "player" : "playerForm";
    this.greetings = `Bonjour ${this.player} !`;
  },
  methods: {
    setPlayer: function(event) {
      let playerName = event.target[0].value;
      if (!playerName) {
        window.alert("Merci de renseigner votre pseudo !");
        return;
      }
      this.player = playerName;
    }
  },
  directives: {
    border: function(el, binding) {
      el.style.borderColor = binding.arg;
    },
    hide: function(el, bindig, vnode) {
      let isForm = vnode.tag === "form";
      let player = vnode.context.player;

      if (isForm) {
        el.style.display = player ? "none" : "block";
      } else {
        el.style.display = player ? "block" : "none";
      }
    }
  }
};
</script>

<style scoped>
/* .player form {
  display: none;
}

.playerForm span {
  display: none;
} */
</style>
