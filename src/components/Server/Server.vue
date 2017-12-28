<template>
  <li class="list-group-item" @click="showDetails()">
    Server #{{ server.id }}
  </li>
</template>

<script>

import {eventBus} from '../../main'

  export default {
    props: {
      server: {
        type: Object
      }
    }, 
    methods: {
      showDetails() {
        eventBus.$emit('serverSelected', this.server)
      }
    }
  }
</script>
