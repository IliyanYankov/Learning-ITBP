<!-- Learning page! -->

<template>
  <i class="fa-solid fa-user-large"></i>
  <Title class="title" title="Welcome"> </Title>
  <i class="fa-solid fa-plus" :class="{ showButton: addTab }"></i>
  <Button
    :class="{ showButton: addTab }"
    @click="toggleForm"
    class="btn"
    value="Add"
  >
  </Button>
  <Table
    class="table"
    @delete-row="deleteRow"
    @update-row="updateRow"
    @click="getElement"
    :class="{ showTable: addTab }"
    :tablesData="tablesData"
  ></Table>
  <i
    :class="{ showButton: !addTab }"
    @click="toggleForm"
    class="fa-solid fa-arrow-left"
  >
  </i>
  <Forms
    :id="id"
    :class="{ showForms: !addTab }"
    @add-course="addCourse"
    :tablesData="tablesData"
  ></Forms>
</template>

<script>
import Table from "../components/learningPage/Table.vue";
import Button from "../components/learningPage/Button.vue";
import Forms from "../components/learningPage/Forms.vue";
import Title from "../components/Title.vue";
import Image from "../components/Image.vue";

export default {
  name: "About",
  components: {
    Table,
    Button,
    Forms,
    Title,
    Image,
  },

  emits: ["delete-row", "update-row"],

  data() {
    return {
      tablesData: [],
      deleteT: false,
      addTab: false,
      updateCondition: false,
      number: 0,
    };
  },

  methods: {
    //Adding new row or editing row
    addCourse(table) {
      //If button Add is clicked ->  Adding new row
      if (!this.updateCondition) {
        this.updateCondition = false;
        this.tablesData = [...this.tablesData, table];
        this.addTab = !this.addTab;
      }
      //If button Edit is clicked - > Editting the row withoud adding new row
      else if (this.updateCondition) {
        this.tablesData = this.tablesData.filter((row) => {
          if (row.id == this.number) {
            table.id = row.id;
            row.courseName = table.courseName;
            row.description = table.description;
            row.lessons = table.lessons;
            row.date = table.date;
            row.imgSrc = table.imgSrc;
          }
          return row.id;
        });
        //Toggle form
        this.addTab = !this.addTab;
      }
    },

    //Toggle  form
    toggleForm() {
      this.addTab = !this.addTab;
    },

    //Delete row
    deleteRow(id) {
      if (confirm(`You are deleting row with ID: ${id}`)) {
        this.tablesData = this.tablesData.filter((row) => {
          return row.id !== id;
        });
      }
    },
    
    //Update button
    updateRow(e) {
      if (confirm("You are going to update data?")) {
        this.addTab = !this.addTab;
        this.updateCondition = true;
        this.number = e;
      }
    },
  },
};
</script>

<style scoped>
body {
  display: flex;
  justify-content: center;
  align-items: center;
}

.title {
  display: flex;
  color: black;
  position: absolute;
  top: 10%;
  left: 10%;
  font-size: 2rem;
  letter-spacing: 0.3rem;
  background-color: grey;
  width: 80%;
  padding: 1%;
  font-weight: 400;
  padding-left: 5%;
}
.fa-user-large {
  display: flex;
  z-index: 3;
  position: absolute;
  top: 11%;

  right: 15%;
  font-size: 3rem;
  color: black;
  border-radius: 50%;
  border: 1px solid;
  border-width: 3px;
  padding-top: 0.3rem;
  padding-left: 0.3rem;
  padding-right: 0.3rem;
  border-bottom: 0.6rem solid black;
}
.fa-arrow-left,
.fa-plus,
.btn {
  background-color: white;
  border: none;
  margin: 0.5rem;
  margin-right: 0;
  font-size: 1.3rem;
  cursor: pointer;
  color: black;
}
.fa-plus {
  cursor: default;
}

.fa-arrow-left {
  position: absolute;
  bottom: 27%;
  left: 40%;
}

.btn:hover {
  text-decoration: underline;
}

.showTable {
  display: none;
}

.showForms {
  display: none;
}

.show {
  display: none;
}
.showButton {
  display: none;
}
@media screen and (max-width: 1500px) {
  .fa-user-large {
    top: 11.5%;
    font-size: 2.5rem;
  }
}

@media screen and (max-width: 1024px) {
  .fa-user-large {
    top: 10.9%;
    font-size: 2rem;
  }
  .fa-arrow-left {
    left: 35%;
  }
  @media screen and (max-width: 500px) {
    .fa-user-large {
      font-size: 1.5rem;
    }
    .fa-arrow-left {
      position: absolute;
      bottom: 27%;
      left: 30%;
    }
  }
}
</style>
