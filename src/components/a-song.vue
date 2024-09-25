<template>
  <div>
    <div class="song">
      <audio
        :src="song.songSrc"
        preload="auto"
        autoplay
        ref="audioPlayer"
      ></audio>
      <!-- <img :src="song.src" /> -->
      <h2>{{ song.name }}</h2>
      <h5>{{ song.artistName }} - {{ song.albumName }} - {{ song.year }}</h5>
      <div>
        <img
          class="gramaphone-casset-image my-4"
          src="/gramaphone casset vactor.jpg"
        />
      </div>
      <div class="controls mt-4">
        <button type="button" class="btn btn-primary" @click="$emit('prev')">
          Prev
        </button>
        <button type="button" class="btn btn-primary mx-3" @click="TogglePlay">
          {{ isPlaying ? "Pause" : "Play" }}
        </button>
        <button type="button" class="btn btn-primary" @click="$emit('next')">
          Next
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "a-song",
  props: {
    song: {
      id: Number,
      name: String,
      artistName: String,
      albumName: String,
      year: Number,
      src: String,
      songSrc: String,
    },
  },
  data() {
    return {
      isPlaying: true,
    };
  },
  methods: {
    TogglePlay() {
      if (this.isPlaying) {
        this.$refs.audioPlayer.pause();
      } else {
        this.$refs.audioPlayer.play();
      }
      this.isPlaying = !this.isPlaying;
    },
  },
};
</script>

<style scoped>
.gramaphone-casset-image {
  height: 200px;
  border-radius: 50%;
  -webkit-animation: spin 4s linear infinite;
  -moz-animation: spin 4s linear infinite;
  animation: spin 4s linear infinite;
}
@-moz-keyframes spin {
  100% {
    -moz-transform: rotate(360deg);
  }
}
@-webkit-keyframes spin {
  100% {
    -webkit-transform: rotate(360deg);
  }
}
@keyframes spin {
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
</style>
