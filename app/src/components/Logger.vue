<script>
  import Contacts from './Contacts'

  export default {
    name: 'logger',
    components: {
      Contacts
    },
    created () {
      this.go = new Date()
      setInterval(() => {
        this.go = new Date()
      }, 1000)
    },
    data () {
      return {
        go: '',
        contact: {},
        no: 1,
        callSign: '',
        callOther: '',
        band: '',
        mode: '',
        rsts: '',
        rstr: '',
        grid: ''
      }
    },
    props: ['contestId', 'contacts'],
    computed: {
      id () {
        if (this.go) {
          if (this.contestId) return this.contestId
          return new Date().toLocaleDateString()
        }
      },
      time () {
        if (this.go) {
          return new Date().toTimeString().split(' ')[0]
        }
      }
    },
    methods: {
      clearProperty (property) {
        this[property] = ''
      }
    }
  }
</script>

<template>
  <div>
    <h3>Contest Information:</h3>
    <span class='contest-info'>
      <p>Date:</p>
      <input
        :value='id'
        @change='updateContestId(id)'
      >
      <p>Callsign</p>
      <input
        :value='callSign'
        v-model='callSign'
      >
    </span>
    <hr>
    <h3>Contact</h3>
    <p>My Call</p>
    <input
      :value='callSign'
    >
    <p>Date</p>
    <input
      :value='id'
    >
    <p>Time</p>
    <input
      :value='time'
    >
    <span>
      <p>Call</p>
      <input
        :value='callOther'
        v-model='callOther'
        @click="clearProperty('callOther')"
      >
    </span>
    <p>Band</p>
    <input
      :value='band'
      v-model='band'
      @click="clearProperty('band')"
    >
    <p>Mode</p>
    <input
      :value='mode'
      v-model='mode'
      @click="clearProperty('mode')"
    >
    <p>RSTs</p>
    <input
      :value='rsts'
      v-model='rsts'
      @click="clearProperty('rsts')"
    >
    <p>RSTr</p>
    <input
      :value='rstr'
      v-model='rstr'
      @click="clearProperty('rstr')"
    >
    <p>Grid</p>
    <input
      :value='grid'
      v-model='grid'
      @click="clearProperty('grid')"
    >
    <hr>
    <h3>Contacts:</h3>
    <contacts :contacts='contacts'></contacts>
  </div>
</template>

<style scoped>
  p {
    display: inline;
  }

  input {
    margin-right: 10px;
    width: 70px;
  }
</style>
