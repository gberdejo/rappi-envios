<template>
  <div class="row">
    <div class="col-md-12">
      <card class="card-plain" body-classes="table-full-width">
        <template slot="header">
          <h4 class="card-title">Lista de numeros telefonicos por atender</h4>
          <p class="category">Here is a subtitle for this table</p>
          <div class="row">
            <div class="col-4">
              <BaseButton :type="'primary'">Agregar numero</BaseButton>
            </div>
          </div>
        </template>
        <el-table
          header-cell-class-name="table-transparent"
          header-row-class-name="table-transparent"
          row-class-name="table-transparent"
          :data="tableData"
        >
          <el-table-column
            min-width="150"
            sortable
            label="Name"
            property="name"
          ></el-table-column>
          <el-table-column
            min-width="150"
            sortable
            label="Country"
            property="country"
          ></el-table-column>
          <el-table-column
            min-width="150"
            sortable
            label="City"
            property="city"
          ></el-table-column>
          <el-table-column
            min-width="150"
            sortable
            align="right"
            header-align="right"
            label="Salary"
            property="salary"
          ></el-table-column>

          <el-table-column min-width="150" align="right" header-align="right">
            <template slot="header">
              <el-input
                v-model="search"
                size="mini"
                placeholder="Type to search"
              />
            </template>
            <template slot-scope="scope">
              <el-button
                size="mini"
                @click="handleEdit(scope.$index, scope.row)"
                >Edit</el-button
              >
              <el-button
                size="mini"
                type="danger"
                @click="handleDelete(scope.$index, scope.row)"
                >Delete</el-button
              >
            </template>
          </el-table-column>
        </el-table>
      </card>
    </div>
  </div>
</template>
<script>
import { Table, TableColumn, Button, Input } from 'element-ui'

export default {
  components: {
    [Table.name]: Table,
    [TableColumn.name]: TableColumn,
    [Button.name]: Button,
    [Input.name]: Input
  },
  data: () => ({
    tableData: [
      {
        id: 1,
        name: 'Dakota Rice',
        salary: '$36.738',
        country: 'Niger',
        city: 'Oud-Turnhout'
      },
      {
        id: 2,
        name: 'Minerva Hooper',
        salary: '$23,789',
        country: 'Curaçao',
        city: 'Sinaai-Waas'
      },
      {
        id: 3,
        name: 'Sage Rodriguez',
        salary: '$56,142',
        country: 'Netherlands',
        city: 'Baileux'
      },
      {
        id: 4,
        name: 'Philip Chaney',
        salary: '$38,735',
        country: 'Korea, South',
        city: 'Overland Park'
      },
      {
        id: 5,
        name: 'Doris Greene',
        salary: '$63,542',
        country: 'Malawi',
        city: 'Feldkirchen in Kärnten'
      }
    ],
    search: ''
  }),
  methods: {
    handleEdit(index, row) {
      console.log(index, row)
    },
    handleDelete(index, row) {
      console.log(index, row)
    }
  },
  watch: {
    search(value, oldvalue) {
      console.log(value, oldvalue)
      this.tableData = this.tableData.filter(
        (data) =>
          !this.search ||
          data.name.toLowerCase().includes(this.search.toLowerCase())
      )
    }
  }
}
</script>
<style>
.table-transparent {
  background-color: transparent !important;
}
</style>
