<template>
  <div class="home">
    <HeaderShayna/>
    <HeroShayna/>
    
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderShayna from '@/components/HeaderShayna.vue'
import HeroShayna from '@/components/HeroShayna.vue'


export default {
  name: 'Home',
  components: {
    HeaderShayna,
    HeroShayna 
  }
}
</script>
