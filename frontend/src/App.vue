<template>
    <div id="app">
        <EchartMap :mapData="mapData" style="width: 100%;height: 100vh" :mapOption="{
            'title': '地图',
            'titleColor': 'pink'
        }"></EchartMap>
    </div>
</template>
<script>
    import EchartMap from './components/EchartMap'
    export default {
        components: {
            EchartMap
        },
        data() {
            return {
                    mapData: []
            }
        },
        methods: {
    initData () {
      this.$ajax.get('http://127.0.0.1:5000/data', {}).then(res => {
        this.mapData = res.data.flight;
      })
    }
  },
  created () {
    this.initData()
  }
    }

</script>
<style>
    * {
        margin: 0;
        padding: 0;
    }

</style>
