<!--Form template for adding data to a table -->

<template>
  <form @submit="onSubmit">
    <input
      v-model="courseName"
      type="text"
      placeholder="Course name"
      required
    />
    <input v-model="description" type="text" placeholder="Description" />
    <input
      v-model="lessons"
      type="number"
      placeholder="Lesson(count)"
      required
    />
    <input v-model="date" type="date" />

    <input ref="inputFile" type="file" @change="preview" />
    <input type="submit" id="button" value="Submit" />
  </form>
</template>

<script>
export default {
  data() {
    return {
      courseName: "",
      description: "",
      date: "",
      lessons: "",
      text: "",
    };
  },

  methods: {
    //Form submitting
    onSubmit(e) {
      e.preventDefault();
      const newTable = {
        id: this.uniqueId(),
        courseName: this.courseName,
        description: this.description,
        date: this.formatDate(this.date),
        lessons: this.lessons,
        imgSrc: this.imgSrc,
      };

      //If validation is true
      if (this.validation()) {
        //Emitting
        this.$emit("add-course", newTable);
        this.resetFieds();
      } else {
        return;
      }
    },

    //Image preview
    preview(e) {
      let imgSrc = URL.createObjectURL(e.target.files[0]);
      this.imgSrc = imgSrc;
    },

    //Date formating
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },

    //Get unique ID
    uniqueId() {
      const id = new Date().getTime();
      return id;
    },

    //Reseting fields
    resetFieds() {
      this.courseName = "";
      this.description = "";
      this.date = "";
      this.lessons = "";
      this.imgSrc = null;
      this.$refs.inputFile.value = null;
    },

    //Input validation!
    validation() {
      const numbers = /^[0-9]+$/;

      if (this.courseName.length <= 3) {
        alert("Course length need to be more than 3 ");
        return false;
      }
      if (this.courseName.match(numbers)) {
        alert("Course must do not contain only number ");
        return false;
      }
      if (this.description.length > 50) {
        alert("Description length must be under 50 ");
        return false;
      }
      if ((this.lessons = 0)) {
        alert("Lessons must be more than 0");
        return false;
      }
      return true;
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  width: 50vw;
  height: 50vh;
}

input {
  margin: auto;
  width: 40%;
  height: 10%;
  border-radius: 5px;
  border: none;
  padding: 10px;
  background-color: rgb(236, 236, 236);
}

input:focus {
  background-color: rgb(255, 255, 255);
}

#button {
  width: 15%;
  background-color: rgb(133, 133, 135);
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  text-align: center;
  letter-spacing: 2px;
  transition: 0.2s ease-in-out;
}

#button:hover {
  width: 17%;
  font-size: 0.95rem;
  background-color: rgb(170, 170, 173);
}
@media screen and (max-width: 1250px) {
  input {
    margin: auto;
    width: 60%;
  }
  #button:hover {
    width: 16%;
  }
}

@media screen and (max-width: 950px) {
  #button {
    width: 35%;
  }
  #button:hover {
    width: 35%;
  }
  input {
    margin: auto;
    width: 100%;
  }
}
</style>
