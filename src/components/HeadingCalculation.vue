<template>
  <div id="heading_calculation" class="h-outer">
    <h1>Heading calculation</h1>
    <p>Click on the question or press ENTER to get answer.</p>
    <p>Click on NEW or press RIGHT to get new questions.</p>
    <div class="h-main" v-if="!showAnswer" @click="toggleClick">
      <div class="main-content">{{ currentHeading }}</div>
      <div class="main-content" v-if="isLeft">Left turn</div>
      <div class="main-content" v-if="!isLeft">Right turn</div>
      <div class="main-content">{{ degreeDifference }}</div>
    </div>
    <div class="h-main" v-if="showAnswer" @click="toggleClick">
      <div class="main-content">{{ answer }}</div>
    </div>
    <button class="main-button" @click="nextQuestion">NEW</button>
  </div>
</template>

<script>
export default {
  name: 'HeadingCalculation',
  data() {
    return {
      updateFlag: 0,
      showAnswer: false,
      currentHeading: 0,
      isLeft: false,
      degreeDifference: 0,
      answer: 0,
    };
  },
  watch: {
    updateFlag: {
      immediate: true,
      handler() {
        this.currentHeading = this.newCurrentHeading();
        this.isLeft = this.newIsLeft();
        this.degreeDifference = this.newDegreeDifference();
        this.answer = this.newAnswer();
      },
    },
  },
  methods: {
    nextQuestion() {
      this.showAnswer = false;
      this.updateFlag += 1;
    },
    toggleClick() {
      this.showAnswer = !this.showAnswer;
    },
    newCurrentHeading() {
      return Math.trunc(Math.random() * 3600000) % 360;
    },
    newIsLeft() {
      return Math.random() < 0.6;
    },
    newDegreeDifference() {
      return (Math.trunc((Math.random() * 100000) / 5) * 5) % 1080;
    },
    newAnswer() {
      return 100;
    },
  },
  created() {
    window.addEventListener('keydown', (e) => {
      if (e.code === 'ArrowRight') {
        this.nextQuestion();
      }
      if (e.code === 'Enter') {
        this.toggleClick();
      }
    });
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
