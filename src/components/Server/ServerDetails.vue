<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="server">Server {{server.id}} is in state {{server.status}}</p>
        <p v-else>Server Details are currently not updated</p>
        <button @click="restore">Restore normality</button>
    </div>

</template>

<script>

import {eventBus} from '../../main';

export default {
  data: function() {
    return {
      server: null
    }
  },
  methods: {
    restore() {
      this.server.status = 'Normal';
      eventBus.$emit('restoreNormality', this.server);
    },
    updateServer(server) {
      this.server = server;
    }
  },
  created() {
    eventBus.$on('serverSelected', this.updateServer)
  }
}
</script>

<style>

</style>
