<template>
  <div id="heading_calculation" class="h-outer">
    <h1>Heading calculation</h1>
    <p>Click on the question or press ENTER to get answer.</p>
    <p>Click on NEW or press RIGHT to get new questions.</p>
    <div class="h-main" v-if="!showAnswer" @click="toggleClick">
      <div class="main-content">72</div>
      <div class="main-content">Left turn</div>
      <div class="main-content">330</div>
    </div>
    <div class="h-main" v-if="showAnswer" @click="toggleClick">
      <div class="main-content">102</div>
    </div>
    <button class="main-button" @click="nextQuestion">NEW</button>
  </div>
</template>

<script>
export default {
  name: 'HeadingCalculation',
  data() {
    return { showAnswer: false };
  },
  methods: {
    nextQuestion() {
      this.showAnswer = false;
    },
    toggleClick() {
      this.showAnswer = !this.showAnswer;
    },
  },
};
</script>

<style scoped lang="scss">
.h-outer {
  display: grid;
}
.h-main {
  cursor: pointer;
  border: solid 1px cornflowerblue;
  min-height: 50vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.main-content {
  font-size: 108px;
}
.main-button {
  justify-self: center;
  padding: 48px;
  font-size: 52px;
}
@media (max-width: 600px) {
  .h-main {
    min-height: 24vh;
  }
  .main-content {
    font-size: 36px;
  }
}
</style>
