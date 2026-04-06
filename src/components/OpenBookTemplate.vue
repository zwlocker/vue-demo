<!-- Design from https://repth.neocities.org/openbook -->
<template>
  <div id="cover">
    <div id="page1">
      <div id="page2">
        <div id="page3">
          <div id="leftpage">
            <slot name="left"></slot>
          </div>
          <div id="rightpage">
            <slot name="right"></slot>
          </div>
          <div id="line" aria-hidden="true" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
#cover {
  width: 820px;
  height: 580px;
  border-radius: 15px;
  background-color: #91697b;
  background-image: url('https://i.imgur.com/BspyVOP.png');
  box-shadow: 2px 2px 2px #57443e;
  padding: 10px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

#page1 {
  background-color: #fff;
  border-radius: 15px;
  width: 818px;
  height: 578px;
  padding: 2px;
  box-shadow: 0px 0px 2px #57443e;
}

#page2 {
  background-color: #fff;
  border-radius: 15px;
  width: 814px;
  height: 574px;
  box-shadow: 0px 0px 2px #574539;
  padding: 2px;
}

#page3 {
  position: relative;
  background-color: #fff;
  border-radius: 15px;
  width: 814px;
  height: 574px;
  box-shadow: 0px 0px 2px #574539;
  background-image: url('https://i.imgur.com/BspyVOP.png');

}

#leftpage {
  float: left;
  width: 363px;
  height: 544px;
  padding: 15px;
}

#rightpage {
  float: right;
  width: 361px;
  height: 544px;
  padding: 15px;
}

#line {
  position: absolute;
  left: 50%;
  top: 0;
  transform: translateX(-50%);
  width: 1px;
  height: 574px;
  margin: 0;
  background-color: #a19386;
  box-shadow: 0px 0px 10px #2e2a27;
  pointer-events: none;
}

#page3::after {
  content: '';
  display: table;
  clear: both;
}
</style>
