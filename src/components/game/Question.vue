<template>
  <div class="card card-default">
    <div class="card-header text-center">
      <h3>{{ this.correctAnswer.key }}</h3>
    </div>
    <div class="card-body">
      <div class="container text-center">
        <div class="row justify-content-between">
          <div
            class="col-5"
            v-for="btn in btnData"
            :key="btn.answer">
            <button
              class="btn btn-info btn-lg"
              style="margin: 10px 0"
              @click="onAnswer(btn.correct)">
              {{ btn.answer }}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    correctAnswer: Object,
    wrongOptions: Array,
  },
  data() {
    return {
      btnData: [
        { correct: false, answer: 1 },
        { correct: false, answer: 2 },
        { correct: false, answer: 3 },
        { correct: false, answer: 4 },
      ],
    };
  },
  mounted() {
    this.generateQuestion();
  },
  methods: {
    generateQuestion() {
      const correctButton = this.generateRandomNumber(0, 3);
      this.btnData.forEach((item, index) => {
        if (index === correctButton) {
          this.btnData[index].correct = true;
          this.btnData[index].answer = this.correctAnswer.value;
        } else {
          this.btnData[index].answer = this.wrongOptions.pop().value;
        }
      });
    },
    generateRandomNumber(min, max) {
      return Math.round(Math.random() * (max - min)) + min;
    },
    onAnswer(isCorrect) {
      this.correctAnswer.isCorrect = isCorrect;
      this.$emit('answered');
    },
  },
};
</script>
