<template>
  <div class="home">
    <Header/>
    <Form/>
  </div>
</template>

<script>
// @ is an alias to /src
import Form from '@/components/Form.vue'
import Header from '@/components/Header.vue'

export default {
  name: 'Home',
  components: {
    Form,
    Header
  }
}
</script>
