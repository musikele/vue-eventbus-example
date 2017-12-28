<template>
  <div class="col-xs-12 col-sm-6">
    <ul class="list-group">
      <my-server v-for="server in servers" :key="server.id" :server="server"></my-server>
      
    </ul>
  </div>
</template>

<script>

import {eventBus} from './../../main'
import Server from './Server.vue'

  export default {
    data: function () {
      return {
        servers: [{
            id: 1,
            status: "Normal"
          },
          {
            id: 2,
            status: "Unknown"
          },
          {
            id: 3,
            status: "Critical"
          },
          {
            id: 4,
            status: "Critical"
          },
          {
            id: 5,
            status: "Unknown"
          }
        ]
      };
    }, 
    components: {
      'my-server': Server
    },
    created() {
      eventBus.$on('restoreNormality', (server) => {
        this.servers.forEach(myServer => {
          if (myServer.id === server.id) {
            myServer.status = server.status; 
          }
        })
      })
    }
  };
</script>

<style>

</style>