<template>
    <div>
        <l-marker v-for="(info, index) in file" :key="index" :lat-lng="[info['lat'], info['lng']]">
            <l-popup>
                <div v-if="info['名称']">
                    <h2>{{info['名称']}}</h2>
                    <table class="table is-bordered">
                        <tr>
                            <th>よみがな</th>
                            <th>所在地</th>
                            <th>問い合わせ</th>
                        </tr>
                        <tr>
                            <td>{{info['読み仮名']}}</td>
                            <td>{{info['所在地']}}</td>
                            <td>{{info['問合せ']}}</td>
                        </tr> 
                    </table>
                </div>
                <div v-if="info['施設名称']">
                    <h2>{{info['施設名称']}}</h2>
                    <p>住所：{{info['郵便番号']}}　{{info['所在地']}}</p>
                    <p>{{info['備考']}}</p>
                    <a :href="info['関連URL']">{{info['関連URL']}}</a>
                </div>
                <div v-if="info['アクセス']">
                    <span>アクセス</span>
                    <p>
                        {{info['アクセス']}}
                    </p>    
                </div>
                
            </l-popup>
        </l-marker>
    </div>
</template>

<script>
    import { LMarker, LPopup } from "nuxt-leaflet";
    export default {
        props: ["file"]
    }
</script>
<style type="text/css">
    a {
        word-wrap: break-word;
    }
</style>