<template>
  <h1>Ag-grid Static Row ID(Not working)</h1>
  <button type="submit" @click="increaseCount">refresh</button>
  <ag-grid-vue class="ag-theme-alpine" :getRowId="getRowId" style="height: 425px" :columnDefs="columnDefs" :rowData="rowData" :defaultColDef="defaultColDef" :gridOptions="gridOptions" @grid-ready="onGridReady"> </ag-grid-vue>
</template>

<script setup>
import { AgGridVue } from 'ag-grid-vue3' // the AG Grid Vue Component
import 'ag-grid-community/styles/ag-grid.css' // Core grid CSS, always needed
import 'ag-grid-community/styles/ag-theme-alpine.css'
import totalValueRenderer from './totalValueRenderer.vue'
import { ref } from 'vue'

const rowData = ref([
  {
    id: 1,
    count: 1
  },
  {
    id: 2,
    count: 2
  },
  {
    id: 3,
    count: 3
  },
  {
    id: 4,
    count: 4
  },
  {
    id: 5,
    count: 5
  },
  {
    id: 6,
    count: 6
  }
])
const getRowId = (params) => {
  // return 'count_' + params.data.count
  return 'id_' + params.data.id
}
const increaseCount = () => {
  const data = rowData.value
  const newData = []
  data.forEach((element) => {
    newData.push({ id: element.id, count: element.count + 1 })
  })
  rowData.value = newData
}
const columnDefs = ref([
  {
    headerName: 'id',
    field: 'id'
  },
  {
    field: 'count'
  },
  {
    headerName: 'Odd Or Even',
    field: 'odd_or_even',
    cellRenderer: totalValueRenderer
  }
])
const defaultColDef = ref({
  initialWidth: 90,
  sortable: false,
  resizable: true
})
const gridOptions = ref({
  rowSelection: 'multiple',
  suppressCellFocus: true,
  suppressRowClickSelection: true,
  isRowSelectable: (params) => {
    return !!params.data && !isNaN(params.data.inNetQuantity) && params.data.inNetQuantity != 0 ? true : false
  }
})
const gridApi = ref(null)
const columnApi = ref(null)
const onGridReady = (params) => {
  try {
    gridApi.value = params.api
    columnApi.value = params.columnApi
    gridApi.value.sizeColumnsToFit() // setting column size
  } catch (error) {
    console.log(error)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
