<script>
  export default {
    data () {
      return {
        partOne: "",
        operator: "",
        partTwo: ""
      }
    },
    methods: {
      inputNumber(e) {
        if (e.target.innerHTML === "AC") {
          this.partOne = ""
          this.operator = ""
          this.partTwo = ""
          return
        }
        else {
          if(e.target.value === "equals") {
            if(this.partOne && this.operator && !this.partTwo) {
              this.operator = ""
            }
            else if(this.partOne && !this.operator && !this.partTwo) {
              return
            }
            else if(this.partOne && this.operator && this.partTwo) {
              if(this.operator === "÷") {
                this.partOne = String(Number(this.partOne) / Number(this.partTwo))
                this.operator = ""
                this.partTwo = ""
              }
              else if(this.operator === "×") {
                this.partOne = String(Number(this.partOne) * Number(this.partTwo))
                this.operator = ""
                this.partTwo = ""
              }
              else if(this.operator === "−") {
                this.partOne = String(Number(this.partOne) - Number(this.partTwo))
                this.operator = ""
                this.partTwo = ""
              }
              else if(this.operator === "+") {
                this.partOne = String(Number(this.partOne) + Number(this.partTwo))
                this.operator = ""
                this.partTwo = ""
              }
              else {
                return
              }
            }
            else {
              return
            }
          }
          else if (this.operator === "") {
            if(e.target.value === "number") {
              this.partOne = this.partOne + e.target.innerHTML
            }
            else if(e.target.value === "dot") {
              if(this.partOne.includes(".")) {
                return
              }
              else {
                this.partOne = this.partOne + "."
              }
            }
            else if(this.partOne && e.target.value === "back") {
              this.partOne = this.partOne.slice(0, -1)
            }
            else if(e.target.value === "operator" && this.partOne) {
              this.operator = e.target.innerHTML
            }
          }
          else if(this.operator) {
            if(e.target.value === "number") {
              this.partTwo = this.partTwo + e.target.innerHTML
            }
            else if(e.target.value === "dot") {
              if(this.partTwo.includes(".")) {
                return
              }
              else {
                this.partTwo = this.partTwo + "."
              }
            }
            else if(this.partTwo && e.target.value === "back") {
              this.partTwo = this.partTwo.slice(0, -1)
            }
            else if(!this.partTwo && e.target.value === "back") {
              this.operator = ""
            }
            else if(e.target.value === "operator" && this.partOne) {
              this.operator = e.target.innerHTML
            }
          }
          else {
            return
          }
        }
      }
    }
  }
</script>

<template>
  <div id="calc">
    <div id="calc-display-container">
      <div id="calc-display">
        <p>{{partOne}}</p>
        <p>{{operator}}</p>
        <p>{{partTwo}}</p>
      </div>
    </div>
    <div id="calc-buttons">
      <div id="calc-number-btns-container">
        <button class="calc-number-btn" value="number" @click="inputNumber">1</button>
        <button class="calc-number-btn" value="number" @click="inputNumber">2</button>
        <button class="calc-number-btn" value="number" @click="inputNumber">3</button>
        <button class="calc-number-btn" value="number" @click="inputNumber">4</button>
        <button class="calc-number-btn" value="number" @click="inputNumber">5</button>
        <button class="calc-number-btn" value="number" @click="inputNumber">6</button>
        <button class="calc-number-btn" value="number" @click="inputNumber">7</button>
        <button class="calc-number-btn" value="number" @click="inputNumber">8</button>
        <button class="calc-number-btn" value="number" @click="inputNumber">9</button>
        <button class="calc-number-btn" value="number" @click="inputNumber">0</button>
        <button class="calc-number-btn calc-flex-btn" value="dot" @click="inputNumber">
          <div id="calc-dot-btn"></div>
        </button>
        <button class="calc-number-btn calc-flex-btn" value="back" @click="inputNumber">
          <div id="calc-back-arrows-container">
            <div id="calc-back-top-arrow"></div>
            <div id="calc-back-bottom-arrow"></div>
          </div>
          <div id="calc-back-btn">x</div>
        </button>
      </div>
      <div id="calc-operator-btns-container">
        <button class="calc-operator-btn" @click="inputNumber">AC</button>
        <button class="calc-operator-btn" value="operator" @click="inputNumber">&divide;</button>
        <button class="calc-operator-btn" value="operator" @click="inputNumber">&times;</button>
        <button class="calc-operator-btn" value="operator" @click="inputNumber">&minus;</button>
        <button class="calc-operator-btn" value="operator" @click="inputNumber">&plus;</button>
        <button class="calc-operator-btn" value="equals" @click="inputNumber">&#x3d;</button>
      </div>
    </div>
  </div>
</template>

<style>
  #calc {
    width: 525px;
    height: 770px;
    border: 1px solid black;
    border-radius: 10px;
  }

  #calc-display-container {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 15%;
    border-bottom: 1px solid black;
    background-color: #1A272C;
  }

  #calc-display {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    align-items: center;
    width: 95%;
    height: 85%;
    background-color: #5FA07B;
    border-radius: 10px;
    padding: 10px;
    overflow: auto;
  }

  #calc-display p {
    font-size: 20px;
    margin-right: 5px;
  }

  #calc-buttons {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: flex-start;
    width: 100%;
    height: 85%;
    padding: 5px;
    background-color: #1A272C;
  }

  #calc-number-btns-container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    width: 80%;
    height: 100%;
    padding: 5px;
    border-right: 1px solid black;
  }

  #calc-operator-btns-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 20%;
    height: 100%;
    padding: 6% 0;
  }

  .calc-number-btn {
    width: 30%;
    height: 15%;
    border: 1px solid black;
    background-color: #6E8187;
    border-radius: 10%;
  }

  .calc-number-btn:hover {
    background-color: #648b97;
    cursor: pointer;
  }

  .calc-operator-btn {
    width: 80%;
    height: 10%;
    text-align: center;
    padding: 11% 0;
    border: 1px solid black;
    background-color: #33638B;
    border-radius: 10%;
  }

  .calc-operator-btn:hover {
    background-color: #2a7ec3;
    cursor: pointer;
  }

  #calc-dot-btn {
    background-color: black;
    width: 8%;
    height: 10%;
    border-radius: 50%;
  }

  .calc-flex-btn {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }

  #calc-back-btn {
    width: 20%;
    height: 20%;
    border: 1px solid black;
    border-left: none;
    padding-bottom: 12%;
    margin-right: 5%;
  }

  #calc-back-arrows-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 10%;
    height: 20%;
    margin-right: -1px;
  }

  #calc-back-top-arrow {
    position: relative;
    bottom: 10%;
    width: 100%;
    height: 50%;
    border-top: 1px solid black;
    transform: rotate(128deg);
  }

  #calc-back-bottom-arrow {
    position: relative;
    top: 10%;
    width: 100%;
    height: 50%;
    border-bottom: 1px solid black;
    transform: rotate(234deg);
  }
</style>