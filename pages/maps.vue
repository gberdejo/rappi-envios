<template>
  <div class="row">
      <div id="map"></div>
  </div>
</template>
<script>
/* eslint-disable */
// import openlayer css for style
import "ol/ol.css";

import * as layer from 'ol/layer';
import * as source from 'ol/source';
import * as geom from 'ol/geom';
import * as style from 'ol/style';
import * as proj from 'ol/proj';
import * as size from 'ol/size';
import * as ol from 'ol';

export default {
  async mounted() {
    await this.initiateMap();
  },
  methods: {
    initiateMap() {
        const map = new ol.Map({
            target: 'map',
            layers: [
                new layer.Tile({
                source: new source.XYZ({
                    url: 'http://www.google.cn/maps/vt/lyrs=r&x={x}&y={y}&z={z}'
                    })
                })
            ],
           view: new ol.View({
                center: proj.fromLonLat([-76.994040,-11.968987]),
                zoom: 15
            })
        })

        const cars = new layer.Vector({
          source: new source.Vector({
            features: [
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-76.977920,-11.960414]))
              }),
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-76.986243,-11.963639]))
              }),
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-77.002640,-11.976343]))
              }),
            ]
          }),
          style: new style.Style({
            image: new style.Icon({
              src: 'https://www.logocrea.com/wp-content/uploads/2016/07/in_transit-256.png',
              width: 40
            })
          })
        })


        const shalomLocals = new layer.Vector({
          source: new source.Vector({
            features: [
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-77.03427819825077,-12.06096086246177]))
              }),
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-76.99906705811469,-12.029888373245145]))
              }),
            ]
          }),
          style: new style.Style({
            image: new style.Icon({
              src: 'https://antonioalcala.com/wp-content/uploads/2018/03/seo-local.png',
              width: 40
            })
          })
        })

        const marvisurLocals = new layer.Vector({
          source: new source.Vector({
            features: [
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-76.99786773610377,-11.965039086851784]))
              }),
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-77.00538659076565,-11.995530322117112]))
              }),
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-77.01238245126392,-12.046555418407]))
              }),
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-77.01271041799782,-12.047502376308023]))
              }),
              new ol.Feature({
                geometry: new geom.Point(proj.fromLonLat([-77.05360392609442,-12.006980799561571]))
              }),
            ]
          }),
          style: new style.Style({
            image: new style.Icon({
              src: 'https://cdn-icons-png.flaticon.com/512/6395/6395603.png',
              width: 40
            })
          })
        })

        map.addLayer(cars)
        map.addLayer(shalomLocals)
        map.addLayer(marvisurLocals)
    },
  },
};
</script>
<style>
</style>