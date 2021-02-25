<template>
  <div class="content-block">
    <h2>Test</h2>
    <div class="dx-card responsive-paddings">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Unde dolor
        repellendus veniam quos! Illo obcaecati amet quo cumque dolore quis quas
        nemo, minima, pariatur molestias deleniti, placeat aspernatur! Aliquid,
        neque.
      </p>
      <br />
      <DxDataGrid
        id="dataGrid"
        :data-source="data"
        key-expr="EmployeeID"
        allow-column-reordering="true"
        loadPanel="true"
      >
        <!-- settings -->
        <DxSelection mode="multiple" />
        <DxFilterRow :visible="true" />
        <DxSearchPanel :visible="true" />
        <DxHeaderFilter :visible="true" />
        <DxGrouping :context-menu-enabled="true" />
        <DxGroupPanel :visible="true" />
        <DxPaging :page-size="5" :page-index="1" />

        <!-- column -->
        <DxColumn
          :allow-header-filtering="false"
          data-field="FullName"
        ></DxColumn>
        <DxColumn data-field="Position"></DxColumn>
        <DxColumn data-field="BirthDate" data-type="date"> </DxColumn>
        <DxColumn data-field="HireDate" data-type="date"> </DxColumn>
        <DxColumn data-field="City" />
        <DxColumn data-field="Country"></DxColumn>
        <DxColumn data-field="Address" />
        <DxColumn data-field="HomePhone" />
        <DxColumn data-field="PostalCode" />
      </DxDataGrid>
    </div>
  </div>
</template>

<script>
import "devextreme/dist/css/dx.common.css";
import "devextreme/dist/css/dx.light.css";
// import axios from "axios";
import service from "../services/employees.service";

import {
  DxDataGrid,
  DxColumn,
  DxFilterRow,
  DxSearchPanel,
  DxHeaderFilter,
  DxPaging,
  DxGrouping,
  DxGroupPanel,
  DxSelection,
} from "devextreme-vue/data-grid";

export default {
  name: "Test",
  components: {
    DxDataGrid,
    DxColumn,
    DxFilterRow,
    DxSearchPanel,
    DxHeaderFilter,
    DxPaging,
    DxGrouping,
    DxGroupPanel,
    DxSelection,
  },
  data() {
    return {
      data: {},
    };
  },
  methods: {
    bindData(Data) {
      this.data = Data;
    },
  },
  mounted() {
    this.bindData(service.getEmployees());
  },
};
</script>

<style>
</style>