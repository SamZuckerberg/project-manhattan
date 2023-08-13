<template>
  <div id="app">
    <div class="max-w-6xl mx-auto sm:px-6 lg:px-8 all">
      <h1 style="color: white;">Quer ficar comigo?</h1>
      <iframe src="silence.mp3" allow="autoplay" id="audio" hidden ></iframe>
      <audio v-if="!yes" src="bonde.mp3" autoplay></audio>
      <audio v-if="yes" src="yes.mp3" autoplay></audio>
      <div class="container" style="height: 50em;">
        <v-btn @click="clickYes" v-model="yes" style="width: 8em; left: -12%; height: 4em;" id="yes">
          Sim
        </v-btn>
        <v-btn @click="clickNo" v-model="no" style="width: 8em; left: 55%; height: 4em; position: absolute" id="no"
          value="Não">
          Não
        </v-btn>
      </div>
    </div>
    <v-img v-if="yes"
      src="https://static1.purebreak.com.br/articles/1/15/07/1/@/74247-confira-memes-super-engra-ccedil-ados-diapo-1.jpg" />
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      yes: false,
      no: false,
    }
  },
  methods: {
    clickYes() {
      const container = document.querySelector('.all');

      container.style.display = 'none';
      this.yes = true;
    },
    clickNo() {
      const noButton = document.getElementById('no');
      const container = document.querySelector('.container');
      const containerWidth = container.clientWidth;
      const containerHeight = container.clientHeight;

      const buttonWidth = noButton.clientWidth;
      const buttonHeight = noButton.clientHeight;

      const randomX = Math.random() * (containerWidth - buttonWidth);
      const randomY = Math.random() * (containerHeight - buttonHeight);

      noButton.style.left = randomX + 'px';
      noButton.style.top = randomY + 'px';
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
