<!-- <script setup>
var h = new Date().getHours();
var m = new Date().getMinutes();
var s = new Date().getSeconds();
var am = "AM";
if (h > 12) {
  h = h - 12;
  var am = "PM";
}
h = h < 10 ? "0" + h : h;
m = m < 10 ? "0" + m : m;
s = s < 10 ? "0" + s : s;

</script> -->

<template>
  <main>
    <div id="clock">
      <h2>The time is now...</h2>
      <div id="time">
        <div>
          <span id="hour">{{ dateTime.h <10 ? "0"+ dateTime.h:dateTime.h }}</span
          ><span>Hours</span>
        </div>
        <div>
          <span id="minutes">{{dateTime.m <10 ? "0"+ dateTime.m:dateTime.m }}</span
          ><span>Minutes</span>
        </div>
        <div>
          <span id="seconds">{{dateTime.s <10 ? "0"+ dateTime.s:dateTime.s}}</span
          ><span>Seconds</span>
        </div>
        <div>
          <span id="ampm">{{ dateTime.am }}</span>
        </div>
      </div>
    </div>
  </main>
</template>
<script>
const date = new Date();
export default {
  name: "App",
  data() {
    return {
      dateTime: {
        h: "",
        m: "",
        s: "",
        am: "AM",
      },
      timer: undefined,
    };
  },
  methods: {
    setDateTime() {
      this.dateTime = {
        h: new Date().getHours(),
        m: new Date().getMinutes(),
        s: new Date().getSeconds(),
      };
      if (this.dateTime.h > 12) {
        this.dateTime.h = this.dateTime.h - 12;
        this.dateTime.am = "PM";
      };
    },
  },
  beforeMount() {
    this.timer = setInterval(this.setDateTime, 1000);
  },
  beforeUnmount() {
    clearInterval(this.timer);
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Open Sans", sans-serif;
}
main {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  background: #060a1f;
}
#clock h2 {
  position: relative;
  display: block;
  color: #fff;
  text-align: center;
  margin: 10px 0;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.4em;
  font-size: 0.8em;
}
#clock #time{
  display: flex;
}
#clock #time div{
  position:relative;
  margin:0 5px;
 -webkit-box-reflect: below 1px linear-gradient(transparent,#0004);
}
#clock #time div span{
  position: relative;
  display: block;
  width: 100px;
  height: 80px;
  background: #688195;
  color: #fff;
  font-weight: 300;
  display:flex;
  justify-content: center;
  align-items: center;
  font-size:3em;
  z-index: 10;
  box-shadow: 0 0 0 1px rgba(0,0,0,2);
}
#clock #time div span:nth-child(2)
{
  height:30px;
  font-size:0.8em;
  font-weight: 300;
  letter-spacing: 0.2em;
  text-transform: uppercase;
}
#clock #time div:nth-last-child(2) span{
  background: #b7587f;
}
#clock #time div:nth-last-child(2) span:nth-child(2){
  background: #812f51;
}
#clock #time div:nth-last-child(1) span{
  position:absolute;
  bottom: 0;
  height:40px;
  font-size: 1.5em;
  -webkit-box-reflect: below 1px linear-gradient(transparent,#0004);
  background: none;
}

</style>
