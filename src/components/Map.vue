<template>
  <div class="map row">
      <div class="col-sm-12">
      <h1>Informations about {{ this.busStopInfo.stop_name }}</h1>
      <p v-if="this.accessible()">This bus stop is designed for wheelchairs users</p>

      <div class="map row">
        <GmapMap
          :center="{lat:this.busStopInfo.stop_coordinates[0], lng:this.busStopInfo.stop_coordinates[1]}"
          :zoom="14"
          map-type-id="roadmap"
          style="width: 100%; height: 700px"
        >
          <GmapMarker :position="{lat: this.busStopInfo.stop_coordinates[0], lng: this.busStopInfo.stop_coordinates[1]}" />
        </GmapMap>
      </div>
    </div>
  </div>
</template>



<script>
const apiURL = 'https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_tan-arrets&q='

export default {
  name: 'Map',
  props: { // parametres entrants
   
  },
  data () {
    return {
      data: null,
      busStopInfo: null
  }},
  created: function () {
    //this.initMarkers()
	},
  mounted () {
    console.log(this.$route.params.id)
    const vm = this
    this.axios
      .get(apiURL + this.$route.params.id)
      .then( response=> (vm.busStopInfo = response.data.records[0].fields))
  },
  methods: {
    accessible: function() {
      if (this.busStopInfo.wheelchair_boarding != "0"){
        return true
      }
      else {
        return false
      }
    },
    intiMap: function() {
      const myLatLng = { lat: -25.363, lng: 131.044 };
      const map = new google.maps.Map(document.getElementById("map"), {
          zoom: 4,
        center: myLatLng,
      });
      new google.maps.Marker({
        position: myLatLng,
        map,
        title: "Hello World!",
     });
    },
    initMarkers: function(){
     
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.map{
  padding: 0% 5% 0% 5%
}
</style>
