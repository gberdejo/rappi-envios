<template>
  <div class="row">
      <div id="map"></div>
  </div>
</template>
<script>
/* eslint-disable */
// import openlayer css for style
import "ol/ol.css";
// This is library of openlayer for handle map
import Map from 'ol/Map';
import View from 'ol/View';
import TileLayer from 'ol/layer/Tile';
import XYZ from 'ol/source/XYZ';
import {fromLonLat} from 'ol/proj'

export default {
  async mounted() {
    await this.initiateMap();
  },
  methods: {
    initiateMap() {
        new Map({
            target: 'map',
            layers: [
                new TileLayer({
                source: new XYZ({
                    url: 'http://www.google.cn/maps/vt/lyrs=r&x={x}&y={y}&z={z}'
                    })
                })
            ],
           view: new View({
                center: fromLonLat([-76.977920,-11.960414]),
                zoom: 15
            })
        })
    },
  },
};
</script>
<style>
#map {
  /* height: 80vh; */
  /* width: 100%; */
}
</style>