<template>
    <div>
        <l-marker v-for="(info, index) in movie" :key="index" :lat-lng="[info['lat'], info['lng']]">
            <l-popup>
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
                <h2>アクセス</h2>
                    <p>
                        {{info['アクセス']}}
                    </p>
            </l-popup>
        </l-marker>
    </div>
</template>

<script>
    import { LMarker, LPopup } from "nuxt-leaflet";
    import movie from '~/assets/368.json'
    export default {
        data(){
            return {movie}
        },
    }
</script>