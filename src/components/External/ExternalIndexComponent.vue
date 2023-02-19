<template>
  <div>
    <h1>Nome : {{ name }}</h1>
  </div>
</template>

<script>
export default {
  name: 'ExternalIndexComponent' ,
  data() {
    return {
      name: "Ainda não informado"
    }
  },
  created() {
    setTimeout(() => {this.name = "Alexandre Ferreira";}, 2000)
  },
  mounted() {
    setTimeout(() => {this.name = "Pedro Silva";}, 4000)
  }
}
</script>
