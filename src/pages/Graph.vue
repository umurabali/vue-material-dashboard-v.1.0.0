<template>
  <div class="content">
    <div class="md-layout">
      <div class="md-layout-item">
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="title">Material Dashboard Heading</h4>
            <p class="category">Created using Roboto Font Family</p>
          </md-card-header>
          <md-card-content>
           Hello!
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>


  export default{
    props: {
      dataBackgroundColor: {
        type: String,
        default: ''
      }
    }
  }
  function onLoad() {
    var g = Viva.Graph.graph();
    g.addNode('1','User name 1');
    g.addNode('2','User name 2');
    g.addNode('3','User name 3');
    g.addLink('1', '2');
    g.addLink('2', '3');
    g.addLink('3', '1');
    var renderer = Viva.Graph.View.renderer(g);
    renderer.run();
    //list each nodes from the graph
    g.forEachNode(function(node){
      console.log(node.id, node.data);
    });
    // show the connected nodes with user id 1
    g.forEachLinkedNode('1', function(linkedNode, link){
      console.log("Connected node: ", linkedNode.id, linkedNode.data);
      console.dir(link); // link object itself
    });
  }

</script>
