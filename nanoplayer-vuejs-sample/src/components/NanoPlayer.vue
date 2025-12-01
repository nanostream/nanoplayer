<!--
nanoStream H5Live Player
(c) 2018-2020, nanocosmos gmbh
http://www.nanocosmos.de
sales@nanocosmos.de
LEGAL NOTICE:
This material is subject to the terms and conditions defined in
separate license conditions ('LICENSE.txt' / nanocosmos.de/terms)
All information contained herein is, and remains the property
of nanocosmos GmbH and its suppliers if any. The intellectual and technical concepts
contained herein are proprietary to nanocosmos GmbH, and are protected by trade secret
or copyright law. Dissemination of this information or reproduction of this material
is strictly forbidden unless prior written permission is obtained from nanocosmos.
All modifications will remain property of nanocosmos.
-->
<template>
  <div class="nano-player-container">
    <h1>NanoStream Vue Player</h1>
    <div ref="playerDiv" id="playerDiv"></div>
    <div v-if="error" class="error-message">
      <p>Error: {{ error }}</p>
    </div>
    <div v-if="loading" class="loading-message">
      <p>Loading player...</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const playerDiv = ref(null)
const error = ref(null)
const loading = ref(true)
let nanoPlayer = null

const config = {
  source: {
    bintu: {
      // Enter your bintu streamid here
      // for more information on how to setup check our API documentation
      // https://docs.nanocosmos.de/docs/nanoplayer/nanoplayer_api/
      streamid: "859b1a11-5458-404a-bd10-5fcd5a9228f1",
    },
  },
  playback: {
    autoplay: true,
    automute: true,
    muted: false,
    flashplayer: "https://demo.nanocosmos.de/nanoplayer/nano.player.swf",
  },
  style: {
    controls: true,
  },
}

onMounted(async () => {
  try {
    if (typeof window.NanoPlayer === 'undefined') {
      throw new Error('NanoPlayer library not loaded')
    }

    nanoPlayer = new window.NanoPlayer("playerDiv")

    const setupResult = await nanoPlayer.setup(config)
    console.log("Setup success")
    console.log("Config:", JSON.stringify(setupResult, null, 2))
    loading.value = false
  } catch (err) {
    console.error('Player setup failed:', err)
    error.value = err.message
    loading.value = false
  }
})

onUnmounted(() => {
  if (nanoPlayer) {
    try {
      nanoPlayer.destroy()
    } catch (err) {
      console.error('Error destroying player:', err)
    }
  }
})
</script>

<style scoped>
.nano-player-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

#playerDiv {
  width: 100%;
  height: 450px;
  background-color: #000;
  border-radius: 8px;
  margin: 20px 0;
}

.error-message {
  color: #d63384;
  background-color: #f8d7da;
  border: 1px solid #f5c2c7;
  border-radius: 4px;
  padding: 12px;
  margin: 20px 0;
}

.loading-message {
  color: #0f5132;
  background-color: #d1e7dd;
  border: 1px solid #badbcc;
  border-radius: 4px;
  padding: 12px;
  margin: 20px 0;
}

h1 {
  color: #333;
  margin-bottom: 20px;
}
</style>
