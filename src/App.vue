<template>
  <div id="app">
    <div class="container">
      <h1>SIN INPUT</h1>
      <div class="countdown">
        <div class="cClock">{{ countdown }}</div>
      </div>
      <button id="countdownButton" v-on:click="countDownTimer()">
        Cuenta regresiva
      </button>
        <h1>INPUT</h1>
      <div class="countdown">
        <input class="cClockInput" type="number" v-model="countdownInput">
      </div>
        <button id="countdownButton" v-on:click="countdownInputTimer()">
          Cuenta regresiva
        </button>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      countdown: 60,
      countdownInput: "",
      countDownTimer() {
        if (this.countdown > 0) {
          setTimeout(() => {
            this.countdown -= 1; // bug: si se sigue presionando el boton, se seguira ejecutando el metoodo sin limite.
            this.countDownTimer();
          }, 1000);
        }
      },
      countdownInputTimer() {
        if (this.countdownInput > 0) {
          setTimeout(() => {
            this.countdownInput -= 1;
            this.countdownInputTimer();
          }, 1000)
        }
      },
    };
  },
};
</script>

<style>
body {
  font-family: sans-serif;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.countdown {
  display: flex;
  flex-direction: row;
}

.cClock {
  text-align: center;
  margin: 0.2em 0.3em;
  padding: 0 0.2em;
  min-width: 1em;
  font-size: 100px;
  border-radius: 20px;
  background-color: #000000;
  color: #ffffff;
}

.cClockInput {
  text-align: center;
  margin: 0.2em 0.3em;
  padding: 0 0.2em;
  max-width: 3em;
  font-size: 100px;
  border-radius: 20px;
  background-color: #000000;
  color: #ffffff;
}

#countdownButton {
  margin-top: 1em;
  height: 30px;
  background-color: #ffffff;
  border: 1px solid lightgray;
  cursor: pointer;
  transition: background-color 0.2s;
}
#countdownButton:hover {
  background-color: lightgray;
}

#countdownButton:active {
  background-color: #808080;
}
</style>
