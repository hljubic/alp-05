<template>
  <div class="about">
    <h1>Novosti</h1>

    <moja-kartica naslov="Novost 1" tekst="U još jednom pogledu smo iskoristili ovu komponetnu."/>
    <moja-kartica naslov="Novost 2" tekst="VueJS se cijeli temelji na komponentama."/>
    <moja-kartica naslov="Novost 3" tekst="To je to. :)"/>
  </div>
</template>

<script>
import MojaKartica from '../components/MojaKartica.vue'

export default {
  components: { MojaKartica },
  name: 'Profile',
}
</script>
