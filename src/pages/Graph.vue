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

          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>


<script>
  import Viva from "../../node_modules/vivagraphjs/dist/vivagraph.js";
  import json from "../sample.json";
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

          
          for(let i = 0; i<json.vertices.length; i++) {
            console.log(json.vertices[i].type);
            if(json.vertices[i].type === "banka") {
              graph.addNode(json.vertices[i]._id);
            }
            else if(json.vertices[i].type === "kisi") {
              graph.addNode(json.vertices[i]._id);
            }
            else if(json.vertices[i].type === "hesap") {
              graph.addNode(json.vertices[i]._id);
            }
          }

          for(let i = 0; i < json.edges.length; i++) {
            if(json.edges[i].type === "hesabi"){
              graph.addLink(json.edges[i].source, json.edges[i].target);
            }
            else if(json.edges[i].type === "aktardi") {

              graph.addLink(json.edges[i].source, json.edges[i].target);
            }
          }



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
