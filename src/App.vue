<template>
<div id="app">
  <h1>{{contadorMin < 10 ? '0'+contadorMin : contadorMin }}:{{contadorSeg < 10 ? '0'+contadorSeg : contadorSeg }} seg</h1>
  <div class="botones">
    <button @click="iniciar(5)">5 seg</button>
    <button @click="iniciar(10)">10 seg</button>
    <button @click="iniciar(30)">30 seg</button>
    <button @click="iniciar(60)">60 seg</button>

  </div>
</div>
</template>

<script>
export default {
  name: "pizza",

  data() {
    return {
      contadorMin: 0,
      contadorSeg: 0,
      myIntervalo: null,
    };
  },

  methods: {
    iniciar(time) {
      this.contadorSeg = time;
      clearInterval(this.myIntervalo);
      this.myIntervalo = setInterval(() => {this.contadorSeg > 0 ? this.contadorSeg-- : false;}, 1000);
      setTimeout(() => {
        clearInterval(this.myIntervalo);
      }, (time + 1) * 1000);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  ul {
    li {
      color: blue;
    }
  }
}
</style>
