<template>

  <div class="content">
    <div class="md-layout">
      <div class="md-layout-item">
        <md-card>

          <md-card-header data-background-color="green">
            <h4 class="title">Material Dashboard Heading</h4>
            <p class="category">Created using Roboto Font Family</p>
          </md-card-header>
          <md-card-content id="invokeGraph">
            <md-button class="md-primary" @click="onLoad()">Bas bana</md-button>
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>


<script>
  import Viva from "../../node_modules/vivagraphjs/dist/vivagraph.js";
   export default{
    props: {
      dataBackgroundColor: {
        type: String,
        default: ''
      }
    },
      methods: {
        onLoad() {
          var graph = Viva.Graph.graph();
          graph.addLink(1, 2, "hi!");
          graph.addLink(2,3);
          graph.addLink(1,3);
          graph.addNode(5);

          var graphics = Viva.Graph.View.webglGraphics();

          var renderer = Viva.Graph.View.renderer(graph,
            {
              graphics : graphics,
              container: document.getElementById('invokeGraph')
            });
          renderer.run();
  }
      },
    mounted() {
      this.onLoad();
    }

    }
</script>

<style type="text/css">
       #invokeGraph{
         height: 500px;
       }
</style>
