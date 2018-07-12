
<template>
  <div>
    <md-table v-model="info" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row"  slot-scope="{ item }">
        <md-table-cell md-label="Company Name">{{ item.companyName }}</md-table-cell>
        <md-table-cell md-label="Address">{{ item.customerAddress }}</md-table-cell>
        <md-table-cell md-label="Item">{{ item.orderedItem }}</md-table-cell>
        <md-table-cell md-label="Cost">{{ item.orderCost }}</md-table-cell>
      </md-table-row>
    </md-table>
    <div style="float:right;margin:10px;">
      <md-button class="md-primary ">Create</md-button>
      <md-button class="md-primary ">Update</md-button>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'simple-table',
  props: {
    tableHeaderColor: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      info: []
    }
  },
  created () {
    axios
      .get('http://localhost:4040/api/orders')
      .then(response => (this.info = response.data))
  }
}
</script>

