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
  <div id="playerDiv"></div>
</template>
<script>
export default {
  name: "NanoPlayer",
  data() {
    return {
      config: {
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
    }
  },
  mounted: function () {
    var nanoPlayer = new NanoPlayer("playerDiv");
    nanoPlayer.setup(this.config).then(
      function (config) {
        console.log("setup success");
        console.log("config: " + JSON.stringify(config, undefined, 4));
      },
      function (error) {
        alert(error.message);
      }
    );
  },
};
</script>
