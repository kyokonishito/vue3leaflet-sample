<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="form-group">
          <label class="col-form-label" for="inputDefault">緯度</label>
          <input type="text" v-model="inputLat" class="form-control" placeholder="緯度" id="inputLat">
        </div>
      </div>
      <div class="col">
        <div class="form-group">
          <label class="col-form-label" for="inputDefault">経度</label>
          <input type="text" v-model="inputLon" class="form-control" placeholder="経度" id="inputLon">
        </div>
      </div>
      <div class="col align-self-end">
        <button type="button" class="btn btn-primary" @click="search">Search</button>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col">
        <div style="height:400px;">
          <l-map ref="map" :zoom="zoom" :use-global-leaflet="false" :center="center" @click="moveMarker">
            <l-tile-layer url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png" layer-type="base"
              name="OpenStreetMap"></l-tile-layer>
            <l-marker :lat-lng="markerLatLng"></l-marker>

          </l-map>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import { LMap, LTileLayer, LMarker } from "@vue-leaflet/vue-leaflet";
export default {
  components: {
    LMap,
    LTileLayer,
    LMarker
  },
  data() {
    return {
      zoom: 15,
      center: [35.6769883, 139.7588499],
      inputLat: 35.6769883,
      inputLon: 139.7588499,
      markerLatLng: [35.6769883, 139.7588499]
    }
  },
  methods: {
    search(e) {
      this.center = [this.inputLat, this.inputLon]
      this.markerLatLng = this.center
    },
    moveMarker(e) {
      if (!e.latlng) { return; }
      this.center = [e.latlng.lat, e.latlng.lng]
      this.markerLatLng = this.center
      this.inputLat=e.latlng.lat
      this.inputLon=e.latlng.lng
    }
  }
}
</script>

<style></style>