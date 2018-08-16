<template>
    <section class="container">
        <section class="hero is-primary is-bold">
          <div class="hero-body">
            <div class="container">
              <h1 class="title">
                観光マップ
              </h1>
              <h2 class="subtitle">
                加古川市の観光名所についてまとめました
              </h2>
              <button class="button is-outlined" @click="changeMap('kankou')">観光名所</button>
              <button class="button is-outlined" @click="changeMap('kanbei')">官兵衛と光ゆかりの史跡</button>
              <button class="button is-outlined" @click="changeMap('movie')">シティプロモーション映画「36.8℃」ロケ地</button>
            </div>
            {{message}}を表示しています。
          </div>
        </section>
        <div id="map" style="width:100%;height: 700px">
            <no-ssr>
                <l-map ref="map" :zoom=13 :center="center">
                    <l-tile-layer url="https://{s}.tile.osm.org/{z}/{x}/{y}.png"></l-tile-layer>>
                    <MapMarker :file="file"/>
                </l-map>
            </no-ssr>
        </div>
    </section>
</template>

<script>
    import { LMap, LTileLayer, LMarker, LIconDefault, LPopup } from "nuxt-leaflet";
    import MapMarker from '~/components/MapMarker'
    import movie from '~/assets/368.json'
    import kanbei from '~/assets/kanbei.json'
    import kankou from '~/assets/60sen.json'
    export default {
        components: {
          MapMarker
        },
        data(){
            return {
                movie,
                kankou,
                kanbei,
                file: kankou,
                message: '加古川の観光地',
                mapname: 'kankou',
                center: [34.757175, 134.841167],
            }
            
        },
        methods: {
            changeMap(val){
                if(val == 'kanbei'){
                    this.file = this.kanbei    
                    this.message = '黒田官兵衛縁の地'
                }
                else if(val == "kankou") {
                    this.file = this.kankou    
                    this.message = '官兵衛と光ゆかりの史跡'
                }
                else if(val == "movie") {
                    this.file = this.movie  
                    this.message = 'シティプロモーション映画「36.8℃」ロケ地'
                }
                
            },
        }
    }
</script>
<style>
    #map {
      width: 500px;
      height: 500px;
    }
</style>