<template>
  <div class="warehoseview">
    <a-scene>

      <a-plane position="0" color="#4CC3D9" depth="0" :height="plant.floor1.floor.height" :width="plant.floor1.floor.width" rotation="-90 0 0"></a-plane>

      <a-box v-for="(aisle,index) in plant.floor1.aisle" v-bind:key="index" :height="aisle.height" :width="aisle.width" :depth="aisle.depth" :color="aisle.color" :position="aisle.startposition.x + ' 5 ' + aisle.startposition.y"></a-box>

    </a-scene>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
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
            }

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
