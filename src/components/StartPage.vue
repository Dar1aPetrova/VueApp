<template>
  <div class="container text-center">
    <div class="card">
      <div class="card-header">
        <h3>Welcome to English Quiz</h3>
      </div>
      <div class="card-body">
        <h5 class="card-title">Start learning English rigth now or edit quiz pack</h5>
        <div class="row justify-content-md-center">
          <div class="col-md-auto">
            <button class="btn btn-info" @click="startGame">START</button>
          </div>
          <div class="col-md-auto">
            <button class="btn btn-info" @click="editPack">EDIT</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    startGame() {
      this.$emit('startGame');
    },
    editPack() {
      this.$emit('editPack');
    },
  },
};
</script>
