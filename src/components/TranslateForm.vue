<template>
  <div class="row" id="translateForm">
    <div class="col-md-3"></div>
    <div class="col-md-6">
      <form v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word.">
        <select class="form-control" v-model="language">
          <option value="zh">Chinese</option>
          <option value="fr">French</option>
          <option value="ru">Russian</option>
          <option value="es">Spanish</option>
        </select>
        <input class="btn btn-primary" type="submit" value="Translate">
      </form>
    </div>
    <div class="col-md-3"></div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data() {
    return {
      textToTranslate: '',
      language: ''
    }
  },
  created() {
    this.language = 'ru';
  },
  methods: {
    formSubmit(e) {
      this.$emit('formSubmit', this.textToTranslate, this.language);
      e.preventDefault();
    }
  }
}
</script>

<style>

.form-control {
  margin-bottom: 1.2rem;
  border-radius: 7px;
}

input[type="text"] {
  padding-left: 0.5rem;
}

.btn {
  border-radius: 7px;
}

.btn-primary:hover {
  background-color: #303133;
  cursor: pointer;
}

</style>