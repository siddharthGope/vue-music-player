<template>
  <div id="App" class="mx-4 my-4">
    <div>
      <button type="button" class="btn btn-primary mb-3" @click="goback">
        Song list
      </button>
      <div v-if="listOfSongs" class="list-of-songs">
        <div>
          <ul
            class="list-group"
            v-for="(item, index) in songList"
            :key="item.id"
          >
            <li class="list-group-item mb-3" @click="playPause(index)">
              <div>
                <h5 class="name">{{ item.name }}</h5>
                <h6 class="artistName">{{ item.artistName }}</h6>
              </div>
            </li>
          </ul>
        </div>
      </div>
      <song
        v-else
        class="song-compo"
        @goback="goback"
        :song="songList[currentSongIndex]"
        @prev="prev"
        @next="next"
      />
    </div>
  </div>
</template>

<script>
import song from "./components/a-song.vue";
export default {
  components: {
    song,
  },
  data() {
    return {
      currentSongIndex: 0,
      listOfSongs: true,
      songList: [
        {
          id: 1,
          name: "Ali Maula",
          artistName: "Shaan",
          albumName: "Le Chakka",
          year: 2024,
        },
        {
          id: 2,
          name: "What If I Told You",
          artistName: "Ali Gatie",
          albumName: "Official",
          year: 2024,
        },
        {
          id: 3,
          name: "Moh Moh Ke Dhaage",
          artistName: "Monali Thakur",
          albumName: "Dum lagake haisha",
          year: 2024,
        },
      ],
    };
  },
  methods: {
    goback() {
      this.listOfSongs = !this.listOfSongs;
    },
    prev() {
      if (this.currentSongIndex != 0) {
        this.currentSongIndex -= 1;
      } else this.currentSongIndex = this.songList.length - 1;
    },
    playPause(index) {
      this.currentSongIndex = index;
      this.listOfSongs = false;
    },
    next() {
      if (this.currentSongIndex < this.songList.length - 1) {
        this.currentSongIndex += 1;
      } else this.currentSongIndex = 0;
    },
  },
};
</script>

<style lang="css" scoped>
.list-group-item {
  width: 50%;
}
</style>
