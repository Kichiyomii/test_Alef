<template>
  <div class="home">
    <Header/>
    <Preview/>
  </div>
</template>

<script>
// @ is an alias to /src
import Preview from '@/components/Preview.vue'
import Header from '@/components/Header.vue'

export default {
  name: 'Home',
  components: {
    Preview,
    Header
  }
}
</script>
