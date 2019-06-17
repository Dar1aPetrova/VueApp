<template>
  <div class="card card-default">
    <div class="card-header text-center">
      <h3>Finish! Here is your result</h3>
        <transition
          appear
          enter-active-class="animated zoomIn delay-1s"
          leave-active-class="animated zoomOut">
          <div class="rating h3">
            <font-awesome-icon
              icon="star"
              size="2x"
              v-for="item in rating"
              :key="item">
            </font-awesome-icon>
          </div>
      </transition>
    </div>
    <ul class="list-group">
      <li
        v-for="question in questionsArray"
        :key="question.key"
        class="list-group-item">
        <div class="row">
          <div class="col-4 text-center"><h4>{{ question.key }}</h4></div>
          <div class="col-4 text-center"><h4>{{ question.value }}</h4></div>
          <div class="col-4 text-center">
            <h4 v-if="question.isCorrect" class="text-success">
              <font-awesome-icon icon="check-circle"/>
            </h4>
            <h4 v-else class="text-danger">
              <font-awesome-icon icon="times-circle"/>
            </h4>
          </div>
        </div>
      </li>
    </ul>
    <div class="card-footer text-center">
      <div class="row justify-content-center">
        <div class="col-md-auto">
          <button class="btn btn-info" @click="goToStart">GO TO START PAGE</button>
        </div>
        <div class="col-md-auto">
          <button class="btn btn-info" @click="startGame">RESTART GAME</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    questionsArray: Array,
  },
  computed: {
    rating() {
      const rightAnswers = this.questionsArray.reduce((acc, current) => {
        if (current.isCorrect) return acc + 1;
        return acc;
      }, 0);
      return Math.max(Math.round(rightAnswers * 5 / this.questionsArray.length), 1);
    },
  },
  methods: {
    startGame() {
      this.$emit('startGame');
    },
    goToStart() {
      this.$emit('goToStart');
    },
  },
};
</script>

<style scoped>
  .rating {
    color: gold;
  }
</style>
