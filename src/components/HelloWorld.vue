<template>
  <div class="warehoseview">
    <a-scene camera look-controls wasd-controls>
    <a-camera :position="camx + ' ' + camy + ' ' +  camz">
      <a-cursor></a-cursor>
    </a-camera>

      <a-plane position="0" color="#4CC3D9" depth="0" :height="plant.floor1.floor.height" :width="plant.floor1.floor.width" rotation="-90 0 0"></a-plane>

      <a-box v-for="(aisle,index) in plant.floor1.aisle" v-bind:key="index" :height="aisle.height" :width="aisle.width" :depth="aisle.depth" :color="aisle.color" :position="aisle.startposition.x + ' 5 ' + aisle.startposition.y">
        <a-box v-for="(section,index2) in aisle.sections" v-bind:key="index2" :height="section.height" :width="section.width"  :color="section.color" :position="section.startposition.x + ' 0 ' + section.startposition.y">
          <a-box  cursor-listener v-for="(shelf,index3) in section.shelves" v-bind:key="index3" :height="shelf.height"  depth="2" :width="shelf.width"  :color="shelf.color" :position="shelf.startposition.x + ' 0 ' + shelf.startposition.y" cursor-listener>

          </a-box>
        </a-box>
      </a-box>

    </a-scene>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      camx:1,
      camy:1,
      camz:1,
      plant: {

        floor1: {
          floor: {
            height: 20,
            width: 20
          },
          aisle: [{
            height: 10,
            width: 10,
            depth: 0.2,
            color: 'red',
            startposition: {
              x: 0,
              y: -10
            }

          },
          {
            height: 10,
            width: 10,
            depth: 0.2,
            color: 'yellow',
            startposition: {
              x: 0,
              y: -5
            }

          }, {
            height: 10,
            width: 10,
            depth: 0.2,
            color: 'blue',
            startposition: {
              x: 0,
              y: 0
            }

          }, {
            height: 10,
            width: 10,
            depth: 0.2,
            color: 'green',
            startposition: {
              x: 0,
              y: 5
            },
              sections:[
                {
                  height: 10,
                  width: 3,
                  color: 'black',
                  startposition: {
                    x: 0,
                    y: 0
                  },
                  shelves:[
                    {  height: 5,
                      width: 3,
                      color: 'white',
                      startposition: {
                        x: 0,
                        y: 0
                      }
                    }
                  ]
                },
                {
                  height: 10,
                  width: 4,
                  color: 'grey',
                  startposition: {
                    x: 4,
                    y: 0
                  }
                }
              ]

          }, {
            height: 10,
            width: 10,
            depth: 0.2,
            color: 'pink',
            startposition: {
              x: 0,
              y: 10
            }

          }
          ]

        }
      }
    }
  },
  mounted(){
    AFRAME.registerComponent('cursor-listener', {
      init: function () {
        var lastIndex = -1;
        var COLORS = ['red', 'green', 'blue'];
        this.el.addEventListener('click', function (evt) {
          alert('shelf clicked, 200 mil tornillos')
        });
      }
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
