<template>
  <div class="outer">
    <span>Height: {{height}}cm</span>
    <input
      type="range"
      class="slider"
      name="height"
      min="100"
      max="220"
      v-model="height"
      @input="calculateBMI()"
      @focus="fixed='height'"
    />
    <span>Weight: {{weight}}kg</span>
    <input
      type="range"
      name="weight"
      min="30"
      max="150"
      v-model="weight"
      class="slider"
      @input="calculateBMI()"
      @focus="fixed='weight'"
    />
    <span>
      BMI: {{bmi}}
      <span :class="isBmiOkay" class="bmi-desc">{{isBmiOkay}}</span>
    </span>
    <input
      type="range"
      name="bmi"
      min="10"
      max="50"
      v-model="bmi"
      class="slider"
      @input="calcSelected()"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      height: 180,
      weight: 80,
      bmi: 24.7,
      fixed: "height"
    };
  },
  computed: {
    isBmiOkay() {
      return this.bmi < 18.5
        ? "underweight"
        : this.bmi > 24.9
        ? "obese"
        : "normal";
    }
  },
  methods: {
    calculateBMI() {
      this.bmi =
        Math.round((this.weight * 10000 * 10) / (this.height * this.height)) /
        10;
    },
    calcSelected() {
      if (this.fixed == "height") {
        this.weight =
          Math.round(((this.height * this.height * this.bmi) / 10000) * 10) /
          10;
      } else {
        this.height =
          Math.round(Math.sqrt((this.weight * 10000) / this.bmi) * 10) / 10;
      }
    }
  }
};
</script>

<style scoped>
.outer {
  display: grid;
  position: relative;
  width: 300px;
  height: 300px;
  background: white;
  border-radius: 5px;
  box-shadow: 0px 20px 50px 0 rgb(0, 0, 0, 0.1);
  justify-content: center;
  text-align: left;
}

.outer:before {
  position: absolute;
  content: "BMI Calculator";
  width: 100%;
  height: 20%;
  font-size: 2rem;
  text-decoration: underline;
  text-align: center;
  border-radius: 5px;
  top: -20%;
  background: white;
}

.underweight {
  color: #dbb900;
}

.normal {
  color: green;
}

.obese {
  color: red;
}

.bmi-desc {
  font-style: oblique;
}
span {
  height: 1rem;
  margin: 0;
}
input {
  height: 1.5rem;
}
</style>