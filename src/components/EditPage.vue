<template>
  <div class="container text-center">
    <div class="card">
      <div class="card-header">
        <h3>Under development</h3>
      </div>
      <div class="card-body">
        <h5 class="card-title">Return to start page</h5>
        <div class="row justify-content-md-center">
          <div class="col-md-auto">
            <button class="btn btn-info" @click="goToStart">START</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    goToStart() {
      this.$emit('goToStart');
    },
  },
};
</script>
