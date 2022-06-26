<!-- Table data template -->

<template>
  <tr>
    <td>
      {{ tablesData.id }}
    </td>
    <td>
      {{ tablesData.courseName }}
    </td>
    <td>
      {{ tablesData.description }}
    </td>
    <td>
      {{ tablesData.lessons }}
    </td>
    <td>
      <button @click="onClick">{{ value }}</button>
    </td>
    <td>
      {{ tablesData.date }}
    </td>
    <td class="image">
      <img :src="tablesData.imgSrc" />
    </td>
    <td class="button">
      <button @click="updateRow(tablesData.id)" class="edit">Edit</button>
      <button @click="deleteRow(tablesData.id)" class="delete">Delete</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "TableData",

  //Get data from Table.vue
  props: {
    tablesData: Object,
  },
  data() {
    return {
      value: "Active",
    };
  },
  methods: {
    //Toggle button active/archive
    onClick(e) {
      console.log(this.tablesData);
      if (this.value === "Active") {
        this.value = "Archieve";
        e.target.style.background = "white";
      } else {
        this.value = "Active";
        e.target.style.background = "#45f745";
      }
    },
    //Get data id, and emit
    deleteRow(id) {
      this.$emit("delete-row", id);
    },
    //Get data id, and emit
    updateRow(id) {
      this.$emit("update-row", id);
    },
  },
};
</script>

<style scoped>
td {
  color: black;
  text-align: center;
  padding: 0.8rem;
  border-left: 1px solid black;
  border-right: 1px solid black;
  border-bottom: 1px solid black;
}

.button {
  display: flex;
  flex-direction: column;
}
.edit,
.delete {
  background-color: white;
  border: none;
  font-size: 1rem;
  cursor: pointer;
}
.edit:hover,
.delete:hover {
  text-decoration: underline;
}

button {
  border: 1px solid black;
  font-size: 1rem;
  border-radius: 5px;
  padding: 0.3rem 0.4rem 0.3rem 0.4rem;
  cursor: pointer;
  background-color: #45f745;
}

.image {
  max-width: 10rem;
}
img {
  width: 55%;
  height: 3rem;
  border-radius: 50%;
  border: none;
}

@media screen and (max-width: 900px) {
  td {
    display: block;
    height: 5rem;
    width: 20rem;
    border-top: 1px solid black;
  }
  .image {
    max-width: 100%;
  }
  img {
    width: 25%;
    height: 4rem;
  }
}
</style>
