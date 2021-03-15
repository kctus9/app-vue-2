<template>
  <div class="home">
    <HelloWorld />
    
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Map from '@/components/Map.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    Map
  },
  data() {//arguments
    return {
      
    }
  }
}
</script>
