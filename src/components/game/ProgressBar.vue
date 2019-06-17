<template>
  <div class="row">
    <div class="col-sm-12">
      <h3>Progress</h3>
        <div class="progress">
          <div
            class="progress-bar bg-info"
            role="progressbar"
            :aria-valuenow="value"
            aria-valuemin="0"
            aria-valuemax="100"
            :style="{width: `${value}%`}">
            {{ currentStep }} / {{ questionsCount}}
          </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['currentStep', 'questionsCount'],
  computed: {
    value() {
      return (this.currentStep / this.questionsCount) * 100;
    },
  },
};
</script>
