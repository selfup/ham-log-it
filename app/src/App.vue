<script>
  import lspi from 'lspi'
  import Logger from './components/Logger'

  export default {
    components: {
      Logger
    },
    data () {
      return {
        contacts: [],
        contests: lspi.get('constest'),
        contestId: ''
      }
    },
    created () {
      const contests = lspi.get('contests')
      if (contests.length > 0) {
        this.contests = contests
        this.contestsId = contests[0].contestsId
        this.contacts = this.contest[this.contestsId]
      } else {
        this.contests = []
        lspi.set('contests', this.contests)
      }
    },
    methods: {
      addContact (contact) {
        this.contacts = [contact, ...this.contacts]
        lspi.set('contacts', this.contacts)
      },
      updateContestId (id) {
        this.contestId = id
      }
    }
  }
</script>

<template>
  <div>
    <logger :contacts='contacts' :contestId='contestId'></logger>
  </div>
</template>

<style>
</style>
