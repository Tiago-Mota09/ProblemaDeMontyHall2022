<template>
  <div id="app">
    <img src="./bandeirinhas.png">
    <h1>Arraiá da Vovó </h1>
    <div class="form">
      <div v-if="!started">
        <label for="portsAmount">Quantas portas?</label>
        <input
          type="text"
          name="portsAmount"
          id="portsAmount"
          size="3"
          v-model.number="portsAmount"
        />
      </div>
      <div v-if="!started">
        <label for="selectedPort">Qual a porta é premiada?</label>
        <input
          type="text"
          name="selectedPort"
          id="selectedPort"
          size="3"
          v-model.number="selectedPort"
        />
      </div>
      <button v-if="!started" @click="started = true">Iniciar</button>
      <button v-if="started" @click="started = false">Reiniciar</button>
    </div>
    <div class="doors" v-if="started">

      <div v-for="i in portsAmount" :key="i">
        <Door :number="i" :hasGift="i === selectedPort"></Door>
      </div>
    </div>
  </div>
</template>

<script>
import Door from "./components/Door";
export default {
  name: "MountHall",
  components: {
    Door,
  },
  data() {
    return {
      started: false,
      portsAmount: 10,
      selectedPort: null,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}

body {
  color: #fff;
  background: linear-gradient(to right, rgb(21, 153, 87), rgb(21, 87, 153));
}
#app > img{
  width:100vw;
  height:600px;
  margin-top: -3em;
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top:50px; 
}
#app h1 {
  border: 1px solid #000;
  background-color: #0006;
  padding: 20px;
  margin: 50px 0 60px;
  border-radius: 5px;
}
.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}
.form,
.form input,
.form button {
  margin: 0 0 20px ;
  font-size: 2rem;
  margin-bottom:60px;
}
.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
