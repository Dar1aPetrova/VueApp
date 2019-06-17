<template>
  <div class="app container">
    <app-header />
    <br><br><br>
    <transition
      mode="out-in"
      faster
      enter-active-class="animated bounceInRight"
      leave-active-class="animated bounceOutLeft">
      <component
        :is="gameMode"
        :questionsArray="questionsArray"
        :trashArray="trashArray"
        @startGame="startGame"
        @finishGame="finishGame"
        @goToStart="goToStart"
        @editPack="goToEdit">
      </component>
    </transition>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import StartPage from './components/StartPage.vue';
import GamePage from './components/GamePage.vue';
import ResultPage from './components/ResultPage.vue';
import EditPage from './components/EditPage.vue';
import questions from './questions';

export default {
  data() {
    return {
      questionsArray: [],
      trashArray: [],
      gameMode: 'app-start-page',
    };
  },
  methods: {
    startGame() {
      this.shuffle(questions);
      this.questionsArray = questions.slice(0, 4);
      this.trashArray = questions.slice(4);
      this.gameMode = 'app-game-page';
    },
    finishGame() {
      this.gameMode = 'app-result-page';
    },
    goToStart() {
      this.gameMode = 'app-start-page';
    },
    goToEdit() {
      this.gameMode = 'app-edit-page';
    },
    shuffle(array) {
      return array.sort(() => Math.random() - 0.5);
    },
  },
  components: {
    'app-header': Header,
    'app-start-page': StartPage,
    'app-game-page': GamePage,
    'app-result-page': ResultPage,
    'app-edit-page': EditPage,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat&display=swap');

.app {
  padding: 24px;
  font-family: 'Montserrat', sans-serif;
}
</style>
