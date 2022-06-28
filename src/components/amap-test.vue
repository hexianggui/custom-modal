<template>
  <div style="position: relative; background-color: white">
    <div id="amapcontainer" style="height: 560px"></div>
  </div>
</template>

<script lang="ts">
import {
  defineComponent,onMounted,ref
} from "vue";


import '@amap/amap-jsapi-loader';
import { load } from '@amap/amap-jsapi-loader';
import '@amap/amap-jsapi-types';
export default defineComponent({
  components: {
  },
  props: {
  },
  setup() {
    const map=ref(null)
     /**
     * 地图导入初始化
     */
    const initMap = async () => {
        const LAMap = await load({ key: 'b7dfe2733f2dc3374e0db408ceb08362', // 申请好的Web端开发者Key，首次调用 load 时必填
        version: '2.0',
        plugins: [
            'AMap.PlaceSearch',
            'AMap.AutoComplete',
            'AMap.Geocoder',
        ],})
        map.value = new LAMap.Map('amapcontainer', { viewMode: '3D',
        // zoom: 20,
        isHotspot: true,
        features: ['bg', 'point', 'road', 'building'], });

    }
    onMounted(()=>{
        initMap()
    })
    return {

    };
  },
});
</script>

<style scoped>
</style>
