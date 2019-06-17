<template>
  <div
    :class="['card',  correctAnswer.isCorrect ? 'border-success' : 'border-danger', 'text-center']">
    <div class="card-body">
      <h1 v-if="correctAnswer.isCorrect" class="card-title text-success">That's Correct!</h1>
      <h1 v-else class="card-title text-danger">Wrong answer!</h1>
      <hr>
      <button
        :class="['btn', correctAnswer.isCorrect ? 'btn-success' : 'btn-danger']"
        @click="onNext">
          Next
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['correctAnswer'],
  methods: {
    onNext() {
      this.$emit('confirmed');
    },
  },
};
</script>
