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
      /* 
        Whether you want to configure a single stream or multiple streams you need to configure them inside the `config.source.entries` object during the initial `setup` call. 
        If secure playback should be used for an ABR multi-stream configuration, a secure token has to be generated for each stream independently. 
        That means that the object `h5live.security` has to be set for each entry. 
        
        Visit our documentation for more information:
          - setup ABR https://docs.nanocosmos.de/docs/nanoplayer/nanoplayer_feature_stream_switching
          - setup secure playback https://docs.nanocosmos.de/docs/nanoplayer/nanoplayer_token_security
          - setup ABR and secure playback https://docs.nanocosmos.de/docs/nanoplayer/nanoplayer_feature_stream_switching/#example-bintu-multi-stream-configuration-with-abr-and-playback-security
          - NanoPlayer API https://docs.nanocosmos.de/docs/nanoplayer/nanoplayer_api

        Example single stream configuration:
        config: {
            "source" : {
                "entries": [
                    {
                        "index": 0,
                        "hls": "",
                        "h5live": {
                            "rtmp": {
                                "url": "rtmp://bintu-play.nanocosmos.de/play",
                                "streamname": "XXXXX-YYYYY"
                            },
                            "server": {
                                "websocket": "wss://bintu-h5live.nanocosmos.de:443/h5live/stream.mp4",
                                "hls": "https://bintu-h5live.nanocosmos.de:443/h5live/http/playlist.m3u8",
                                "progressive": "https://bintu-h5live.nanocosmos.de:443/h5live/http/stream.mp4"
                            },
                            "token": "",
                            "security": {}
                        },
                        "bintu": {}
                    }
                ]
            },
            "playback": {
                ...
            },
            "style": {
                ...
            }
        };
    
        Example multi stream configuration (with ABR)
          config: {
            "source" : {
                "entries": [ // array of 'entry' objects
                    {
                        "index": 0,
                        "hls": "",
                        "h5live": {
                            "rtmp": {
                                "url": "rtmp://bintu-play.nanocosmos.de/play",
                                "streamname": "XXXXX-YYYY0"
                            },
                            "server": {
                                "websocket": "wss://bintu-h5live.nanocosmos.de:443/h5live/stream.mp4",
                                "hls": "https://bintu-h5live.nanocosmos.de:443/h5live/http/playlist.m3u8",
                                "progressive": "https://bintu-h5live.nanocosmos.de:443/h5live/http/stream.mp4"
                            },
                            "token": "",
                            "security": {}
                        },
                        "bintu": {}
                    },
                    {
                        "index": 1,
                        "hls": "",
                        "h5live": {
                            "rtmp": {
                                "url": "rtmp://bintu-play.nanocosmos.de/play",
                                "streamname": "XXXXX-YYYY1"
                            },
                            "server": {
                                "websocket": "wss://bintu-h5live.nanocosmos.de:443/h5live/stream.mp4",
                                "hls": "https://bintu-h5live.nanocosmos.de:443/h5live/http/playlist.m3u8",
                                "progressive": "https://bintu-h5live.nanocosmos.de:443/h5live/http/stream.mp4"
                            },
                            "token": "",
                            "security": {}
                        },
                        "bintu": {}
                    },
                    {
                        "index": 2,
                        "hls": "",
                        "h5live": {
                            "rtmp": {
                                "url": "rtmp://bintu-play.nanocosmos.de/play",
                                "streamname": "XXXXX-YYYY2"
                            },
                            "server": {
                                "websocket": "wss://bintu-h5live.nanocosmos.de:443/h5live/stream.mp4",
                                "hls": "https://bintu-h5live.nanocosmos.de:443/h5live/http/playlist.m3u8",
                                "progressive": "https://bintu-h5live.nanocosmos.de:443/h5live/http/stream.mp4"
                            },
                            "token": "",
                            "security": {}
                        },
                        "bintu": {}
                    }
                ],
                "options": {
                    "adaption": {
                        "rule": "deviationOfMean" // enable ABR
                    },
                    "switch": {
                        'method': 'server',
                        'pauseOnError': false,
                        'forcePlay': true,
                        'fastStart': false,
                        'timeout': 10,
                    }
                },
                "startIndex": 2 // lowest
            },
            "playback": {
                ...
            },
            "style": {
                ...
            }
        };
      */

      config: {
        source: {
          entries: [
            {
              index: 0,
              hls: "",
              h5live: {
                rtmp: {
                  url: "rtmp://bintu-play.nanocosmos.de/play",
                  streamname: "HX26g-NRbx9",
                },
                server: {
                  websocket:
                    "wss://bintu-play.nanocosmos.de:443/h5live/stream.mp4",
                  hls:
                    "https://bintu-play.nanocosmos.de:443/h5live/http/playlist.m3u8",
                  progressive:
                    "https://bintu-play.nanocosmos.de:443/h5live/http/stream.mp4",
                },
                token: "",
                security: {},
              },
              bintu: {},
            },
            {
              index: 1,
              hls: "",
              h5live: {
                rtmp: {
                  url: "rtmp://bintu-play.nanocosmos.de/play",
                  streamname: "HX26g-uVn3M",
                },
                server: {
                  websocket:
                    "wss://bintu-play.nanocosmos.de:443/h5live/stream.mp4",
                  hls:
                    "https://bintu-play.nanocosmos.de:443/h5live/http/playlist.m3u8",
                  progressive:
                    "https://bintu-play.nanocosmos.de:443/h5live/http/stream.mp4",
                },
                token: "",
                security: {},
              },
              bintu: {},
            },
            {
              index: 2,
              hls: "",
              h5live: {
                rtmp: {
                  url: "rtmp://bintu-play.nanocosmos.de/play",
                  streamname: "HX26g-VbAxm",
                },
                server: {
                  websocket:
                    "wss://bintu-play.nanocosmos.de:443/h5live/stream.mp4",
                  hls:
                    "https://bintu-play.nanocosmos.de:443/h5live/http/playlist.m3u8",
                  progressive:
                    "https://bintu-play.nanocosmos.de:443/h5live/http/stream.mp4",
                },
                token: "",
                security: {},
              },
              bintu: {},
            },
          ],
          options: {
            adaption: {
              rule: "deviationOfMean",
            },
            switch: {},
          },
          startIndex: 2,
        },
        playback: {
          autoplay: true,
          automute: true,
          muted: true,
          flashplayer: "//demo.nanocosmos.de/nanoplayer/nano.player.swf",
        },
        style: {
          displayMutedAutoplay: true,
        },
      },
    };
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
