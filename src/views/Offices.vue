<template>
  <div class="offices">
    <div class="container-fluid">
      <div class="row">
        <div class="col-xs-12 col-lg-6 offices__right">
          <h2 class="offices__caption">Our Offices</h2>
          <ul class="offices__tabs">
            <li class="offices__tabs-list"><a :class="[country === 'Ukraine' ? 'active' : '']" @click.prevent="changeCountry('Ukraine', 50.45466, 30.5238)" class="offices__tabs-link" href="#">Kyiv</a></li>
            <li class="offices__tabs-list"><a :class="[country === 'USA' ? 'active' : '']" @click.prevent="changeCountry('USA', 40.730610, -73.935242)" class="offices__tabs-link" href="#">New York</a></li>
            <li class="offices__tabs-list"><a :class="[country === 'China' ? 'active' : '']" @click.prevent="changeCountry('China', 23.128994, 113.253250)" class="offices__tabs-link" href="#">Guangzhou</a></li>
            <li class="offices__tabs-list offices__tabs-list--last"><a :class="[country === 'Spane' ? 'active' : '']" @click.prevent="changeCountry('Spane', 41.390205, 2.154007)" class="offices__tabs-link" href="#">Barcelona</a></li>
          </ul>
          <div>
            <h3 class="offices__subcaption">Global Message Services {{country}} LLC</h3>
            <ul v-for="(office, index) in getOffices" :key="index" class="offices__address">
              <li class="offices__text">{{office.address}}</li>
              <li class="offices__text">{{office.zip_code}}</li>
              <li class="offices__text offices__text--last">{{office.country}}</li>
            </ul>
          </div>
        </div>
        <div id="map" class="col-xs-12 col-lg-6 offices__left">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'offices',
  data() {
    return {
      coordinates: {
        lat: 50.45466,
        lng: 30.5238
      },
      country: 'Ukraine',
      offices: [
        {
          address: 'Kuiv, Stepan Bandera, 33',
          zip_code: '02066',
          country: 'Ukraine'
        },
        {
          address: 'New York',
          zip_code: '10001',
          country: 'USA'
        },
        {
          address: 'Guangzhou',
          zip_code: '510000',
          country: 'China'
        },
        {
          address: 'Barcelona',
          zip_code: '08001',
          country: 'Spane'
        }
      ]
    }
  },
  computed: {
    getOffices() {
      switch(this.country) {
        case 'Ukraine': return this.offices.slice(0, 1)
        break;
        case 'USA': return this.offices.slice(1, 2)
        break;
        case 'China': return this.offices.slice(2, 3)
        break;
        case 'Spane': return this.offices.slice(3, 4)
        break;
        default: return this.offices.slice(0, 1)
      }
    }
  },
  methods: {
    initMap() {
      const map = new google.maps.Map(document.getElementById('map'), {
        center: {lat: this.coordinates.lat, lng: this.coordinates.lng},
        zoom: 12,
        disableDefaultUI: true,
        styles: [
          {
            "elementType": "geometry",
            "stylers": [
              {
                "color": "#212121"
              }
            ]
          },
          {
            "elementType": "labels.icon",
            "stylers": [
              {
                "visibility": "off"
              }
            ]
          },
          {
            "elementType": "labels.text.fill",
            "stylers": [
              {
                "color": "#757575"
              }
            ]
          },
          {
            "elementType": "labels.text.stroke",
            "stylers": [
              {
                "color": "#212121"
              }
            ]
          },
          {
            "featureType": "administrative",
            "elementType": "geometry",
            "stylers": [
              {
                "color": "#757575"
              }
            ]
          },
          {
            "featureType": "administrative.country",
            "elementType": "labels.text.fill",
            "stylers": [
              {
                "color": "#9e9e9e"
              }
            ]
          },
          {
            "featureType": "administrative.land_parcel",
            "stylers": [
              {
                "visibility": "off"
              }
            ]
          },
          {
            "featureType": "administrative.locality",
            "elementType": "labels.text.fill",
            "stylers": [
              {
                "color": "#bdbdbd"
              }
            ]
          },
          {
            "featureType": "poi",
            "elementType": "labels.text.fill",
            "stylers": [
              {
                "color": "#757575"
              }
            ]
          },
          {
            "featureType": "poi.park",
            "elementType": "geometry",
            "stylers": [
              {
                "color": "#181818"
              }
            ]
          },
          {
            "featureType": "poi.park",
            "elementType": "labels.text.fill",
            "stylers": [
              {
                "color": "#616161"
              }
            ]
          },
          {
            "featureType": "poi.park",
            "elementType": "labels.text.stroke",
            "stylers": [
              {
                "color": "#1b1b1b"
              }
            ]
          },
          {
            "featureType": "road",
            "elementType": "geometry.fill",
            "stylers": [
              {
                "color": "#2c2c2c"
              }
            ]
          },
          {
            "featureType": "road",
            "elementType": "labels.text.fill",
            "stylers": [
              {
                "color": "#8a8a8a"
              }
            ]
          },
          {
            "featureType": "road.arterial",
            "elementType": "geometry",
            "stylers": [
              {
                "color": "#373737"
              }
            ]
          },
          {
            "featureType": "road.highway",
            "elementType": "geometry",
            "stylers": [
              {
                "color": "#3c3c3c"
              }
            ]
          },
          {
            "featureType": "road.highway.controlled_access",
            "elementType": "geometry",
            "stylers": [
              {
                "color": "#4e4e4e"
              }
            ]
          },
          {
            "featureType": "road.local",
            "elementType": "labels.text.fill",
            "stylers": [
              {
                "color": "#616161"
              }
            ]
          },
          {
            "featureType": "transit",
            "elementType": "labels.text.fill",
            "stylers": [
              {
                "color": "#757575"
              }
            ]
          },
          {
            "featureType": "water",
            "elementType": "geometry",
            "stylers": [
              {
                "color": "#000000"
              }
            ]
          },
          {
            "featureType": "water",
            "elementType": "labels.text.fill",
            "stylers": [
              {
                "color": "#3d3d3d"
              }
            ]
          }
        ]
      });
      new google.maps.Marker({
        position: {lat: this.coordinates.lat, lng: this.coordinates.lng},
        map: map,
        icon: {
          path: google.maps.SymbolPath.CIRCLE,
          fillColor: '#3db565',
          fillOpacity: 1,
          strokeColor: '#3db565',
          strokeOpacity: 1,
          strokeWeight: 1,
          scale: 10
        }
      });
      return map
    },
    changeCountry(country, lat, lng) {
      this.country = country;
      this.coordinates.lat = lat;
      this.coordinates.lng = lng
    }
  },
  watch: {
    'coordinates.lat': {
      handler() {
        this.initMap()
      }
    }
  },
  mounted() {
    this.initMap()
  }
}
</script>


<style lang="scss" scoped>

.offices {
  background: #252525;
  padding-left: 60px;
  &__tabs {
    display: flex;
    margin-bottom: 53px;
    &-list {
      margin-right: 21px;
      &--last {
        margin-right: 0;
      }
    }
  }
  &__tabs-link {
    font-weight: 600;
    color: #ffffff;
    text-transform: uppercase;
  }
  &__caption {
    font-weight: 300;
    font-size: 34px;
    line-height: 48px;
    color: #ffffff;
    margin-bottom: 48px;
  }
  &__subcaption {
    margin-bottom: 34px;
    font-weight: 300;
    font-size: 26px;
    line-height: 20px;
    color: #ffffff;
  }
  &__right {
    padding: 96px 0;
  }
  &__text {
    font-weight: 400;
    color: #ffffff;
  }
}

.active {
  color: #3db565;
}

@media screen and(max-width: 768px) {
  .offices {
    text-align: center;
    padding-left: 0;
    &__left {
      min-height: 500px;
    }
    &__text {
      margin-bottom: 10px;
    }
    &__right {
      padding: 46px 0;
    }
    &__tabs {
      justify-content: center;
      flex-direction: column;
      &-list {
        margin-right: 0;
        margin-bottom: 21px;
        &--last {
          margin-bottom: 0;
        }
      }
    }
  }
}

@media screen and(max-width: 576px) {
  .offices {
    &__caption {
      margin-bottom: 20px;
    }
    &__subcaption {
      line-height: 30px;
    }
  }
}
</style>