<template>
  <div class="about">
    <h1>This is an profile page. My name is Marko.</h1>

    <zbroji-brojeve broj1="37" broj2="57"/>
    
    <moja-kartica naslov="Prva kartica" tekst="Moja prva komponenta u VueJS-u."/>
    <moja-kartica naslov="Druga kartica" tekst="Moja druga komponenta u VueJS-u."/>
    <moja-kartica naslov="Treća kartica" tekst="Moja treća komponenta u VueJS-u."/>
  </div>
</template>

<script>
import MojaKartica from '../components/MojaKartica.vue'
import ZbrojiBrojeve from '../components/ZbrojiBrojeve.vue'

export default {
  components: { MojaKartica, ZbrojiBrojeve },
  name: 'Profile',
}
</script>
