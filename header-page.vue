<template>
  <header>
    <div class="logo">
      <img src="../assets/images/photo1.png" />
      <p>{{ $t("header1") }}</p>
    </div>
    <div class="contacts">
      <span class="lnr lnr-phone-handset"></span>
      <p>{{ $t("header2") }}<br /></p>
    </div>
    <div class="locate">
      <span class="lnr lnr-map-marker"></span>
      <p>
        {{ $t("header3") }}
      </p>
    </div>
    <div class="locales">
      <span class="lnr lnr-earth"></span>
      <div>
        <select v-model="$i18n.locale" @click="upd()">
          <option
            v-for="locale in $i18n.availableLocales"
            :key="`locale-${locale}`"
            :value="locale"
          >
            {{ locale }}
          </option>
        </select>
      </div>
    </div>

    <div class="menu">
      <a class="primary-nav-trigger" @click="open()">
        <span class="menu-icon"></span>
      </a>
    </div>
  </header>

  <div :style="show ? filterStyle : null" class="offnav" id="vv">
    <div class="toper">
      <span class="lnr lnr-cross vv" @click="close()"></span>
    </div>
    <div class="mainer">
      <div class="main1">
        <span class="lnr lnr-phone-handset"></span>
        <p>
          {{ $t("header2") }}
        </p>
        <p></p>
      </div>
      <div class="main2">
        <span class="lnr lnr-map-marker"></span>
        <p>
          {{ $t("header3") }}
        </p>
      </div>
      <div class="main3">
        <div><span class="lnr lnr-earth"></span></div>
        <select v-model="$i18n.locale" @click="upd()">
          <option
            v-for="locale in $i18n.availableLocales"
            :key="`locale-${locale}`"
            :value="locale"
          >
            {{ locale }}
          </option>
        </select>
      </div>
      <div class="main4">
        <p>Patio Style Furniture Manufacturing LLC,</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "header-page",
  data() {
    return {
      show: false,
      filterStyle: {
        position: "fixed",
        right: "0%",
        top: "0",
        background: "rgb(15, 55, 0)",
        height: "100%"
      },
    };
  },
  methods: {
    upd(localStorage) {
      console.log(localStorage);
      console.log("work");
    },
    open() {
      this.show = !this.show;
    },
    close() {
      this.show = !this.show;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 select {
      width: auto;
      height: auto;
      padding: 0.5vmin 1vmin;
      border-radius:4px;
      box-shadow: 2px 2px 8px rgba(15, 55, 0, 0.4);
      background: #fff;
      border: none;
      outline: none;
      display: inline-block;
      -webkit-appearance:none;
      -moz-appearance: none;
      appearance: none;
      cursor: pointer;
      margin-left: 1.2vmin;
      }
      label {
      position: relative;
      }
      label:after {
      content:'<>';
      font: 11px "Consolas", monospace;
      color: #666;
      -webkit-transform: rotate(90deg);
      -moz-transform: rotate(90deg);
      -ms-transform: rotate(90deg);
      transform: rotate(90deg);
      right: 8px; 
      top:2px;
      padding: 0 0 2px;
      border-bottom: 1px solid #ddd;
      position: absolute;
      pointer-events: none;
      }
      label:before {
      content: '';
      right: 6px; 
      top:0px;
      width: 20px; 
      height: 20px;
      background: #eee;
      position: absolute;
      pointer-events: none;
      display: block;
      }
      @media (max-width: 920px) {
select {
  margin-left: 0;
}

       }
</style>
