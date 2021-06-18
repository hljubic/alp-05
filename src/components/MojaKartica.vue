<template>
  <div class="card">
    <h1>{{ naslov }}</h1>

    <p class="card-text">
      {{ tekst }}
    </p>
  </div>
</template>

<script>
export default {
  name: 'MojaKartica',
  props: ['naslov', 'tekst']
}
</script>

<style>
.card {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 10px;
  border-radius: 3px;
  box-shadow: #2c3e50;
}
.card-text {
  margin-top: 30px;
}
</style>
