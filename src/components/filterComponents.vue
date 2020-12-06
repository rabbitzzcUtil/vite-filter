<template>
  <div class="filter-component">
    <div class="filter-main">
      <div class="filter-wrapper filter-edit">
        <div class="single single-first">
          <div class="show">
            <span>blur</span>
            <output>{{filters.blur}}</output>
          </div>
          <input
            type="range"
            min="0"
            max="10"
            step="0.1"
            v-model="filters.blur"
          >
        </div>
        <div class="single">
          <div class="show">
            <span>brightness</span>
            <output>{{filters.brightness}}</output>
          </div>
          <input
            type="range"
            min="0"
            max="3"
            step="0.1"
            v-model="filters.brightness"
          >
        </div>
        <div class="single">
          <div class="show">
            <span>contrast</span>
            <output>{{filters.contrast}}</output>
          </div>
          <input
            type="range"
            min="0"
            max="3"
            step="0.1"
            v-model="filters.contrast"
          >
        </div>
        <div class="single">
          <div class="show">
            <span>grayscale</span>
            <output>{{filters.grayscale}}</output>
          </div>
          <input
            type="range"
            min="0"
            max="1"
            step="0.01"
            v-model="filters.grayscale"
          >
        </div>
        <div class="single">
          <div class="show">
            <span>hueRotate</span>
            <output>{{filters.hueRotate}}</output>
          </div>
          <input
            type="range"
            min="0"
            max="360"
            step="1"
            v-model="filters.hueRotate"
          >
        </div>
        <div class="single">
          <div class="show">
            <span>invert</span>
            <output>{{filters.invert}}</output>
          </div>
          <input
            type="range"
            min="0"
            max="1"
            step="0.01"
            v-model="filters.invert"
          >
        </div>
        <div class="single">
          <div class="show">
            <span>opacity</span>
            <output>{{filters.opacity}}</output>
          </div>
          <input
            type="range"
            min="0"
            max="1"
            step="0.01"
            v-model="filters.opacity"
          >
        </div>
        <div class="single">
          <div class="show">
            <span>saturate</span>
            <output>{{filters.saturate}}</output>
          </div>
          <input
            type="range"
            min="0"
            max="3"
            step="0.1"
            v-model="filters.saturate"
          >
        </div>
        <div class="single">
          <div class="show">
            <span>sepia</span>
            <output>{{filters.sepia}}</output>
          </div>
          <input
            type="range"
            min="0"
            max="1"
            step="0.01"
            v-model="filters.sepia"
          >
        </div>
        <div class="single">
          <div class="show">
            <span>drop-shadow</span>
          </div>
          <textarea
            placeholder="drop-shadow"
            v-model="filters.dropShadow"
          ></textarea>
        </div>
        <div class="img-input">
          <textarea
            placeholder="图片链接/img src"
            v-model="imgUrl"
          ></textarea>
        </div>
      </div>
      <div class="filter-wrapper filter-preview">
        <div class="img-wrapper">
          <img
            :style="filterCode"
            :src="imgUrl"
            alt=""
          >
        </div>
      </div>
    </div>
    <hr>
    <div class="css-code">
      <h2>CSS code</h2>
      <code>{{filterCode}}</code>
      <code>{{'-webkit-filter' + filterCode.slice(6) }}</code>
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            filters: {
                blur: 0,
                brightness: 1,
                contrast:1,
                grayscale: 0,
                'hueRotate': 0,
                invert: 0,
                opacity: 1,
                saturate: 1,
                sepia: 0,
                dropShadow: '8px 8px 10px #ccc'
            },
            imgUrl: 'http://h2.ioliu.cn/bing/ChipmunkJP_ZH-CN1697070440_1920x1080.jpg?imageslim'
        }
    },
    computed:{
        filterCode() {
            let code = 'filter:'
            const {blur, brightness,contrast,grayscale,hueRotate,invert,opacity,saturate,sepia,dropShadow} = this.filters
            if(blur !== 0) code += ` blur(${blur}px)`
            if(brightness !== 1) code += ` brightness(${brightness})`
            if(contrast !== 1) code += ` contrast(${contrast})`
            if(grayscale !== 0) code += ` grayscale(${grayscale})`
            if(hueRotate !== 0) code += ` hue-rotate(${hueRotate}deg)`
            if(invert !== 0) code += ` invert(${invert})`
            if(opacity !== 1) code += ` opacity(${opacity})`
            if(saturate !== 1) code += ` saturate(${saturate})`
            if(sepia !== 0) code += ` sepia(${sepia})`
            if(dropShadow !== '') code += ` drop-shadow(${dropShadow})`

            
            return code + ';'
        }
    },
    methods:{},

}
</script>

<style scoped>
input[type="range"] {
  width: 100%;
  height: 2px;
  border-radius: 5px;
  background: #d7dcdf;
  outline: none;
  padding: 0;
  margin: 0;
}

.filter-component {
  width: 80vw;
  margin: 0 auto;
}

.filter-main {
  display: flex;
}
.filter-wrapper {
  flex: 1;
  padding: 10px;
}

.show {
  display: flex;
  justify-content: space-between;
}

.show {
  color: gray;
  font-size: x-small;
}

.single {
  margin: 15px 0;
}

.single-first {
    margin-top: 0;
}

.img-wrapper {
  margin: 0;
  padding: 0;
  position: relative;
  width: 500px;
  /* height: 500px; */
}
.img-wrapper img {
  width: 100%;
  height: 100%;
}

.img-input textarea,
.single textarea {
  margin-top: 0px;
  margin-bottom: 0px;
  min-height: 24px;
  resize: vertical;
  text-align: left;
  width: 100%;
}

.css-code code {
  display: block;
  padding: 5px;
  background: #000;
  color: #eee;
}
</style>