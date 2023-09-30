<template>
  <div>
    <div class="background-pie"></div>
    <div class="set-size charts-container">
      <div class="pie-wrapper progress-30">
        <span class="label">
          <span class="text-label">
            <span class="smaller">lvl</span><span class="level-text">{{ level }}</span>
            <span class="exp-text">{{ exp }} / {{ level * 10 }} </span>
          </span>
        </span>
        <div class="pie">
          <div class="left-side half-circle"></div>
        </div>
      </div>
    </div>
    <div class="main-menu-class">
      <div class="row" v-for="i in colors.length / 2">
        <div class="column">
          <div class="menu-button" :style="computedStyle(i - 1)" @click="onClickFunctions(i - 1)"
            @touchstart="onClickFunctions(i - 1)">
            {{ categories[i - 1] }}
          </div>
        </div>
        <div class="column">
          <div class="menu-button" :style="computedStyle(colors.length - i)"
            @click="onClickFunctions(categories.length - i)" @touchstart="onClickFunctions(categories.length - i)">
            {{ categories[categories.length - i] }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
const colors = ['#16213E', '#0F3460', '#533483', '#E94560', '#451952', '#662549', '#AE445A', '#F39F5A'];
const categories = ['Flags', 'General', 'Sports', 'History', 'Judaism', 'Capitals', 'Music', 'Reality'];
export default {
  name: 'main-menu-component',
  props: ['level', 'exp'],
  data() {
    return {
      colors: colors,
      categories: categories
    }
  },
  methods: {
    computedStyle(i) {
      return { '--my-color': colors[i] }
    },
    onClickFunctions(index) {
      this.$emit('start-game');
    }
  }
}
</script>
<style scoped>
.main-menu-class {
  padding-top: 25vh;
  padding-bottom: 20vh;
}

.menu-button {
  background: var(--my-color);
  height: 10vh;
  width: 20vh;
  margin-left: auto;
  margin-right: auto;
  margin-top: 2vh;
  margin-bottom: 2vh;
  border-radius: 8px;
  color: white;
  font-size: 3vh;
  font-weight: 500;
  align-items: center;
  line-height: 10vh;
  text-align: center;
  box-shadow: rgba(0, 0, 0, 0.4) 0px 10px 10px, rgba(0, 0, 0, 0.3) 0px 35px 38px -40px, rgba(0, 0, 0, 0.2) 0px -15px 0px inset;
}

.row {
  display: flex;
}

.column {
  flex: 50%;
}

.charts-container:after {
  clear: both;
  content: "";
  display: table;
}

*,
*:before,
*:after {
  box-sizing: border-box;
}

html,
body {
  background: #ecf0f1;
  color: #444;
  font-family: "Lato", Tahoma, Geneva, sans-serif;
  font-size: 16px;
  padding: 10px;
}

.set-size {
  font-size: 18vh;
}

.charts-container:after {
  clear: both;
  content: "";
  display: table;
}

.charts-container:after {
  clear: both;
  content: "";
  display: table;
}

.pie-wrapper {
  height: 1em;
  width: 1em;
  float: left;
  position: absolute;
  left: 30vw;
  top: 2vh;
  z-index: 2;
}

.pie-wrapper:nth-child(3n+1) {
  clear: both;
}

.pie-wrapper .pie {
  height: 100%;
  width: 100%;
  clip: rect(0, 1em, 1em, 0.5em);
  left: 0;
  position: absolute;
  top: 0;
}

.pie-wrapper .pie .half-circle {
  height: 100%;
  width: 100%;
  border: 0.1em solid #533483;
  border-radius: 50%;
  left: 0;
  position: absolute;
  z-index: 1;
  top: 0;
}

.pie-wrapper .label {
  background: #16213E;
  border-radius: 50%;
  bottom: 0.4em;
  color: #ecf0f1;
  cursor: default;
  display: block;
  font-size: 0.25em;
  left: 0.4em;
  line-height: 2.8em;
  position: absolute;
  right: 0.4em;
  text-align: center;
  top: 0.4em;
  box-shadow: inset 10px -10px 25px rgba(0, 0, 0, 0.6);

}

.text-label {
  position: relative;
  z-index: 1;
}

.level-text {
  text-align: center;
  padding: 1vh;
  margin: 1vh;
}

.pie-wrapper .label .smaller {
  color: #bdc3c7;
  font-size: 0.45em;
  padding-bottom: 20px;
  vertical-align: super;
}

.exp-text {
  font-size: 1vh;
  vertical-align: sub;
}

.pie-wrapper .shadow {
  height: 100%;
  width: 100%;
  border: 0.1em solid #bdc3c7;
  border-radius: 50%;
}

.pie-wrapper.style-2 .label {
  background: none;
  color: #126d74;
}

.pie-wrapper.style-2 .label .smaller {
  color: #bdc3c7;
}

.pie-wrapper.progress-30 .pie {
  clip: rect(auto, auto, auto, auto);
}

.pie-wrapper.progress-30 .pie .half-circle {
  border-color: #533483;
  box-shadow: inset 0 0px 0px 4px #b58fed;

}

.pie-wrapper.progress-30 .pie .left-side {
  transform: rotate(180deg);
}

.pie-wrapper.progress-30 .pie .right-side {
  transform: rotate(216deg);
}

.fill-pie {
  background: cornflowerblue;
  height: 11vh;
  width: 18vh;
  top: 5vh;
  border-radius: 50%;
  z-index: 0;
  position: relative;
}

.background-pie {
  background: #282828;
  position: absolute;
  z-index: 2;
  height: 18vh;
  width: 18vh;
  left: 30vw;
  top: 2vh;
}</style>