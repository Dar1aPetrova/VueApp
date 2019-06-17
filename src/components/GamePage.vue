<template>
  <div class="container">
    <app-progress-bar :currentStep="currentStep" :questionsCount="questionsArray.length"/>
    <br>
    <div class="row justify-content-md-center">
      <div class="col-md-6">
        <transition
          mode="out-in"
          enter-active-class="animated fadeIn faster"
          leave-active-class="animated fadeOut faster">
          <component
            :is="mode"
            :correctAnswer="questionsArray[currentStep]"
            :wrongOptions="trashArray.slice(currentStep*3, currentStep*3+3)"
            @answered="answered($event)"
            @confirmed="next">
          </component>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import ProgressBar from './game/ProgressBar.vue';
import Question from './game/Question.vue';
import Answer from './game/Answer.vue';

export default {
  props: {
    questionsArray: Array,
    trashArray: Array,
  },
  data() {
    return {
      mode: 'app-question',
      currentStep: 0,
    };
  },
  components: {
    appQuestion: Question,
    appAnswer: Answer,
    appProgressBar: ProgressBar,
  },
  methods: {
    answered() {
      this.mode = 'app-answer';
    },
    next() {
      this.currentStep += 1;
      if (this.currentStep === this.questionsArray.length) {
        this.$emit('finishGame');
      } else {
        this.mode = 'app-question';
      }
    },
  },
};
</script>
