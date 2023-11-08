<template>
  <div>
    <h1>{{ message }}</h1>
    <button @click="this.$emit('button-click')">CLick me</button>
  </div>
</template>

<script>
export default {
  name: 'ChildComponent',
  props: {
    message: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped></style>
