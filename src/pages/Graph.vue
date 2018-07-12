<template>

  <div class="content">
    <div class="md-layout">
      <div id="md-layout-item">
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="title">Graph of finance data</h4>
            <p class="category">UNDER DEVELOPMENT!!!</p>
          </md-card-header>
          <md-card-content>

          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>


<script>
  import ForceGraph from 'force-graph';
  import json from "../sample.json";
  console.log(json);
   export default{
    props: {
      dataBackgroundColor: {
        type: String,
        default: ''
      }
    },
      methods: {

      onLoad(){
        let graph = ForceGraph();
        graph(document.getElementById("md-layout-item"))
          .graphData(json)
          .nodeId('id')
          .nodeAutoColorBy('type')
          .linkSource('source')
          .linkTarget('target');
      }
    },
      mounted() {
        console.log("DONE");
        this.onLoad();
     }


   }

</script>

<style type="text/css">
    md-card-content {
      margin: auto;
    }
</style>
