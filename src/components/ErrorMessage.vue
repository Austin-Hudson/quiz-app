<script>
  export default{
    name: "ErrorMessage",
    props: {
      message: String
  }
}

</script>

<template>
  <p class="error-message"> {{ message }} </p>
</template>

<style scoped>
  .error-message {
    color: #B22222;
  }
</style>
