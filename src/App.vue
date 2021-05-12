<template>
  <div id="app">
    <div class="portrait">
      <img :src="image" alt="歌手肖像"/>
    </div>
    <SongList :data="dataSource"></SongList>
  </div>
</template>

<script>
import axios from 'axios'
import SongList from '@/components/SongList'

export default {
  components: {
    SongList
  },
  data() {
    return {
      dataSource: [],
      image: null
    }
  }
  ,
  created() {
    axios
        .get('http://localhost:3000/artists?id=3684')
        .then((data) => {
          const img = data.data.artist.picUrl
          const newData = data.data.hotSongs.map((item) => ({
            id: item.id,
            name: item.name,
            ar: item.ar.map((arItem) => arItem.name).join('/'),
            al: {
              name: item.al.name,
              picUrl: item.al.picUrl,
            },
          }))
          this.dataSource = newData
          this.image = img
        })
        .catch((error) => console.log(error))
  }
}
</script>

<style lang="scss">
@keyframes rotate {
  0% {
    transform: rotate(0);
  }
  100% {
    transform: rotate(360deg);
  }
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

li {
  list-style: none;
}

.portrait {
  width: 100vw;
  height: 60vh;

  img {
    width: 100%;
  }
}
</style>
