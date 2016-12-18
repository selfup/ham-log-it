<script>
  import ContactHead from './ContactHead'

  export default {
    components: {
      ContactHead
    },
    name: 'contacts',
    props: ['contacts']
  }
</script>

<template>
  <div>
    <contact-head v-if='contacts.length > 0'></contact-head>
  </div>
</template>

<style scoped>
</style>
