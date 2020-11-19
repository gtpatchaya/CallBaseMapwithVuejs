<template>
<div>

  <div  id="map"></div>
  
</div>
</template>

<script>
var nostra = window.nostra;
export default {
    name: 'NostraMap',  
    data () 
        {
            return {
                map: {},
                baseMapCountry : "TH",                      
        }
    },
    beforeCreate: function () {
        console.log("before create")
            nostra.onready = function () {
            nostra.config.Language.setLanguage(nostra.language.E);           
        };  
    },
    mounted() {
       window.setTimeout(this.sleepTime  , 3000); 
    },
    methods : {
        sleepTime(){
            console.log('XX')
            this.initialize();
        },
        initialize() {
            console.log("initiailize")
            var  map =  new nostra.maps.Map("map", {
                    id: "map",
                    logo: true,
                    scalebar: true,
                    basemap: "streetmap",
                    slider: true,   
                    level: 15,
                    lat: 13.722944,
                    lon: 100.530449,
                    country: "TH"
                });  

            map.events.layerAddComplete = function () 
            {
                    console.log('compleate')
            };

            // console.log(basemapObj)
            // var basemapObj = new nostra.maps.layers.OpenStreetMap(map);
            // map.addLayer(basemapObj);
        }  
    }
}
</script>



<style>

#map{
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
}

</style>