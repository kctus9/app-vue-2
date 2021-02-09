<template>
  <div class="home">
    <HelloWorld :msg="msg"/>
    <Test/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Test from '@/components/Test.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    Test
  },
  data() {//arguments
    return {
      msg: "Alexis"
    }
  }
}
</script>
