<template>
    <div>
        <div class="set-size charts-container">
            <div class="pie-wrapper progress-30">
                <span class="label"><span class="smaller">lvl</span>1</span>
                <div class="pie">
                    <div class="left-side half-circle"></div>
                    <div class="right-side half-circle"></div>
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
                        @click="onClickFunctions(categories.length - i)"
                        @touchstart="onClickFunctions(categories.length - i)">
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
            debugger;
            this.$emit('start-game');
        }
    }
}
</script>
<style scoped>
.main-menu-class {
    padding-top: 20vh;
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
  font-size: 10em;
}

.charts-container:after {
  clear: both;
  content: "";
  display: table;
}
.set-size {
  font-size: 10em;
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
  margin: 15px;
  position: absolute;
  left: 11vh;
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
  clip: rect(0, 0.5em, 1em, 0);
  left: 0;
  position: absolute;
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
  box-shadow: inset  10px -10px 25px rgba(0,0,0,0.6);

}
.pie-wrapper .label .smaller {
  color: #bdc3c7;
  font-size: 0.45em;
  padding-bottom: 20px;
  vertical-align: super;
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
  transform: rotate(216deg);
}
.pie-wrapper.progress-30 .pie .right-side {
  transform: rotate(180deg);
}
</style>