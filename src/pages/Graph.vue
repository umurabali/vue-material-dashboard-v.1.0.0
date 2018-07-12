<template>

  <div class="content">
    <div class="md-layout">
      <div class="md-layout-item">
        <div id="graphContainer"></div>
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
        let highlightNodes = [];
        let highlightLink = null;
        const elem = document.getElementById('graphContainer');
        let graph = ForceGraph();
        graph(elem)
          .graphData(json)
          .nodeId('id')
          .nodeAutoColorBy('type')
          .linkSource('source')
          .linkTarget('target')
          .linkDirectionalParticles(2)
          .onNodeHover(node => {
          highlightNodes = node ? [node] : [];
          elem.style.cursor = node ? '-webkit-grab' : null;
        })
          .onLinkHover(link => {
            highlightLink = link;
            highlightNodes = link ? [link.source, link.target] : [];
          });
      }
    },
      mounted() {
        console.log("DONE");
        this.onLoad();
     }
   }

</script>
