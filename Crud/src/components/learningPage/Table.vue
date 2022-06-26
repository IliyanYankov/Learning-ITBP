<!-- Table view -->

<template>
  <div id="table-wrapper">
    <div id="table-scroll">
      <table>
        <thead>
          <tr>
            <th><span class="text">ID</span></th>
            <th><span class="text">Course name</span></th>
            <th><span class="text">Description</span></th>
            <th><span class="text">Lessons(count)</span></th>
            <th><span class="text">State</span></th>
            <th><span class="text">Date added</span></th>
            <th><span class="text">Image</span></th>
            <th><span class="text">Edit/Delete</span></th>
          </tr>
        </thead>
        <!-- Printing table body -->
        <tbody :key="tables.id" v-for="tables in tablesData">
          <TableData
            @delete-row="$emit('delete-row', tables.id)"
            @update-row="$emit(`update-row`, tables.id)"
            :tablesData="tables"
          ></TableData>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import Button from "../learningPage/Button.vue";
import TableData from "../learningPage/TableData.vue";
export default {
  name: "Table",
  components: {
    Button,
    //Get data from Learning.vue
    TableData,
  },
  props: {
    tablesData: [],
  },
};
</script>

<style scoped>
#table-scroll {
  height: 300px;
  overflow: auto;
}

#table-wrapper {
  color: black;
}
#table-wrapper table thead th .text {
  display: flex;
  z-index: 2;
  border: 1px solid black;
  padding: 0.5rem 1rem 0.5rem 1rem;
  text-align: center;
  justify-content: center;
}

@media screen and (max-width: 900px) {
  #table-wrapper table thead {
    display: none;
  }
}
</style>
