<template>
  <div id="calc">
    <div id="display">
      <input
        type="text"
        id="number"
        name="name"
        placeholder="Enter Equation"
        v-model="formula"
        v-on:keyup.delete="backspace()"
        v-on:keyup.enter="evaluate()"
      />

      <h1>{{ this.formula }}</h1>
    </div>

    <div id="buttons">
      <b-container class="calc">
        <b-row>
          <b-col sm="3" id="num7">
            <b-button @click="append(7)"> 7 </b-button></b-col
          >
          <b-col sm="3" id="num8"
            ><b-button @click="append(8)"> 8 </b-button></b-col
          >
          <b-col sm="3" id="num9">
            <b-button @click="append(9)"> 9 </b-button></b-col
          >
          <b-col sm="3" id="division">
            <b-button @click="append('/')"> ÷ </b-button></b-col
          >
        </b-row>

        <b-row>
          <b-col sm="3" id="num4">
            <b-button @click="append(4)"> 4 </b-button></b-col
          >
          <b-col sm="3" id="num5">
            <b-button @click="append(5)"> 5 </b-button>
          </b-col>
          <b-col sm="3" id="num6">
            <b-button @click="append(6)"> 6 </b-button></b-col
          >
          <b-col sm="3" id="multiply">
            <b-button @click="append('*')"> × </b-button></b-col
          >
        </b-row>
        <b-row>
          <b-col sm="3" id="num1"
            ><b-button @click="append(1)"> 1 </b-button></b-col
          >
          <b-col sm="3" id="num2"
            ><b-button @click="append(2)"> 2 </b-button></b-col
          >
          <b-col sm="3" id="num3"
            ><b-button @click="append(3)"> 3 </b-button></b-col
          >
          <b-col sm="3" id="subtract">
            <b-button @click="append('-')"> - </b-button>
          </b-col>
        </b-row>
        <b-row>
          <b-col sm="4" id="num0">
            <b-button id="num" @click="append(0)"> 0 </b-button></b-col
          >
          <b-col sm="4" id="decimal">
            <b-button @click="append('.')"> . </b-button></b-col
          >
          <b-col sm="4" id="add">
            <b-button @click="append('+')"> + </b-button></b-col
          >
        </b-row>

        <b-row>
          <b-col sm="4" id="num0">
            <b-button @click="backspace()"> Backspace</b-button></b-col
          >
          <b-col sm="4" id="decimal">
            <b-button @click="clear()"> Clear </b-button></b-col
          >
          <b-col sm="4" id="add">
            <b-button @click="evaluate()"> Enter </b-button></b-col
          >
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      enterPressed: "",
      formulaAlert: "",
      formula: "",
    };
  },
  methods: {
    evaluate() {
      this.enterPressed = true;
      console.log(this.enterPressed);

      try {
        let result = eval(this.formula);
        this.formulaAlert = false;
        this.formula = result;
        console.log(this.formula);
      } catch (exception) {
        this.formulaAlert = true;
      }
    },

    append(value) {
      if ((this.enterPressed = true)) {
        if (this.formula.length == 0) {
          this.formula = value;
        } else {
          var temp = this.formula;
          temp = temp.toString() + value.toString();
          this.formula = temp;
        }
      }
      // TODO
    },

    clear() {
      this.formula = "";
    },

    backspace() {
      if ((this.enterPressed = true)) {
        var temp = this.formula;
        temp.toString();
        this.formula = temp.slice(0, -1);
      }
    },
  },
};
</script>

<style>
#calc {
  background: #0b2f4f;
}
#display {
  background-color: #ffffff;
  border: solid;
  height: 150px;
  min-width: 500px;
  margin-bottom: 10px;
}
input {
  height: 50px;
  min-width: 510px;
  border: none;
}

input[type="text"] {
  font-size: 20px;
}

.row {
  height: 100px;
  margin-top: 5px;
  margin-bottom: 5px;
  margin-right: 0px;
}

#actions {
  margin-top: 5px;
  border: none;
}

#clear {
  margin-right: 5px;
}
p {
  text-align: center;
  font-size: 50px;
}
.col {
  margin-right: 5px;
}
.col-4 button {
  margin: 0px;
  width: 270px;
}
button {
  height: 100px;
  width: 100px;
}

.btn {
  background: #0b2f4f; /* light background with opacity 50% */

  /* black border */
  color: #ffffff; /* white text */
  border-radius: 5px; /* rounded corners */
  font-size: 22px; /* larger fonts */
  cursor: pointer; /* make it look clickable */
}

#num0 {
  width: 225px;
  margin-right: 25px;
}

#num0 button {
  width: 225px;
}
.col-sm-4 {
  width: 100px;
  margin-right: 25px;
}
.col-sm-4 button {
  width: 100px;
}

#num {
  margin-right: 40px;
}
</style>
