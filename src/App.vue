<template>
  <div id="app">
    <VPlayer ref="videoPlayer" :playerOptions="vOption" id="player" />
  </div>
</template>

<script>
import VPlayer from "./components/Player.vue";

export default {
  name: "App",
  components: {
    VPlayer,
  },
  data() {
    return {
      vOption: {
        type: "",
        src: "", //视频地址
        volume:20,
        preload: true, //是否预下载，默认为true
        autoplay: true, //是否自动播放（兼容性不太好），默认为false
        isLoop: false, //是否循环，默认不循环
        playsinline: true,
        poster: "", //封面，仅视频有
        crossOrigin: false, //设置视频的 CORS 设置。
      },
    };
  },
  mounted() {
    this.vOption.type = "application/x-mpegURL";
    this.vOption.poster = "https://img.inengjian.com/default_pic/50ec61d4-e069-421d-83ca-0d4c1a625067.jpg?imageView2/0/format/webp/q/75";
    this.vOption.src = "http://ivi.bupt.edu.cn/hls/dftv.m3u8";
    this.$refs.videoPlayer.initMedaData();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
*{
  margin: 0;
  padding: 0;
}
html,body,#app{
  width: 100%;
  height: 100%;
}
#player{
  width: 100%;
  height: auto;
}
</style>
