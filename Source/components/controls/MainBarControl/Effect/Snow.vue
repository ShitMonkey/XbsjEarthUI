<template>
  <div class="xbsj-mainbar-popup popup">
    <div class="row">
      <label class="label" @click="alpha=0">{{lang.alpha}}:</label>
      <div class="field">
        <XbsjSlider :min="0" :max="1" :step="0.1" showTip="always" v-model="alpha"></XbsjSlider>
      </div>
    </div>
    <!-- <div class="row">
      <label class="label" @click="emissionRate=5000">{{lang.fssl}}:</label>
      <div class="field">
        <XbsjSlider :min="1" :max="10000" :step="1" showTip="always" v-model="emissionRate"></XbsjSlider>
      </div>
    </div>
    <div class="row">
      <label class="label" @click="startScale=1">{{lang.csdx}}:</label>
      <div class="field">
        <XbsjSlider :min="0.1" :max="5" :step="0.1" showTip="always" v-model="startScale"></XbsjSlider>
      </div>
    </div>

    <div class="row">
      <label class="label" @click="endScale=0">{{lang.zzdx}}:</label>
      <div class="field">
        <XbsjSlider :min="0.1" :max="5" :step="0.1" showTip="always" v-model="endScale"></XbsjSlider>
      </div>
    </div>
    <div class="row">
      <label class="label">{{lang.ksys}}:</label>
      <div class="colorstartDiv">
        <XbsjColorButton ref="colorButton" v-model="uistartcolor"></XbsjColorButton>
      </div>
      <label class="label">{{lang.zzys}}:</label>
      <div class="colorendDiv">
        <XbsjColorButton ref="colorButton" v-model="uiendcolor"></XbsjColorButton>
      </div>
    </div>-->

    <!-- <div class="row">
      <label class="label">终止颜色:</label>
      <div class="colorendDiv">
        <XbsjColorButton ref="colorButton" @toColor="toColor"></XbsjColorButton>
      </div>
    </div>-->
  </div>
</template>

<script>
export default {
  data() {
    return {
      langs: {
        zh: {
          // fssl: "发射速率",
          // csdx: "初始大小",
          // zzdx: "终止大小",
          // ksys: "开始颜色",
          // zzys: "终止颜色",
          alpha: "积雪程度"
        },
        en: {
          // fssl: "fssl",
          // csdx: "csdx",
          // zzdx: "zzdx",
          // ksys: "ksys",
          // zzys: "zzys",
          alpha: "alpha"
        }
      },
      lang: undefined,
      // emissionRate: 7000.0,
      // startScale: 0.5,
      // endScale: 1.0,
      // startColor: [],
      // endColor: [],
      // uistartcolor: undefined,
      // uiendcolor: undefined,
      alpha: 0.6
    };
  },
  created() {},
  mounted() {
    // this.bind("emissionRate");
    // this.bind("startScale");
    // this.bind("endScale");
    // this.bind("startColor");
    // this.bind("endColor");
    this.bind("alpha");
  },
  methods: {
    bind(prp) {
      this._viewUnbinds = this._viewUnbinds || [];
      this._viewUnbinds.push(
        XE.MVVM.bind(this, prp, this.$root.$earth.weather.snowPostProcess, prp)
      );
    }
  },
  watch: {
    // uistartcolor(scolor) {
    //   var sv = scolor.rgba;
    //   var scc = [sv.r / 255.0, sv.g / 255.0, sv.b / 255.0, sv.a];
    //   if (!this.startColor.every((sc, index) => sc === scc[index])) {
    //     this.startColor = scc;
    //   }
    // },
    // startColor(sc) {
    //   this.uistartcolor = {
    //     rgba: {
    //       r: sc[0] * 255,
    //       g: sc[1] * 255,
    //       b: sc[2] * 255,
    //       a: sc[3]
    //     }
    //   };
    // },
    // uiendcolor(ecolor) {
    //   var ev = ecolor.rgba;
    //   var ecc = [ev.r / 255.0, ev.g / 255.0, ev.b / 255.0, ev.a];
    //   if (!this.endColor.every((ec, index) => ec === ecc[index])) {
    //     this.endColor = ecc;
    //   }
    // },
    // endColor(ec) {
    //   this.uiendcolor = {
    //     rgba: {
    //       r: ec[0] * 255,
    //       g: ec[1] * 255,
    //       b: ec[2] * 255,
    //       a: ec[3]
    //     }
    //   };
    // }
  },
  beforeDestroy() {
    this._viewUnbinds.forEach(u => u());
    this._viewUnbinds.length = 0;
  }
};
</script>

<style scoped>
.popup {
  width: 310px;
  min-height: 60px;
}

.label {
  display: inline-block;
  width: 52px;
  text-align: right;
  margin-right: 5px;
  vertical-align: top;
  line-height: 29px;
}
.row {
  margin-top: 10px;
}
.field {
  padding-left: 4px;
  display: inline-block;
  width: 220px;
}
.colorstartDiv,
.colorendDiv {
  display: inline-block;
}
.colorstartDiv {
  margin-right: 30px;
}
</style>