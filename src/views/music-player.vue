<template>
  <div>
    <div v-if="listOfSongs" class="list-of-songs">
      <div>
        <ul
          class="list-group"
          v-for="(item, index) in listOfSongs"
          :key="index"
        >
          <li class="list-group-item">
            <div class="name">{{ item.name }}</div>
            <div class="artistName">{{ item.artistName }}</div>
            <!-- <img v-bind:src="item.src" /> -->
          </li>
        </ul>
      </div>
    </div>
    <div v-else class="song-compo">Songs</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      listOfSongs: true,
      songList: [
        {
          id: 1,
          name: "Cheap Thrills",
          artistName: "Adam Lambert",
          albumName: "Everything",
          year: 2021,
          src: "https://unsplash.com/photos/selective-focus-silhouette-photography-of-man-playing-red-lighted-dj-terminal-YrtFlrLo2DQ",
          songSrc: "/audio/Ali Maula.mp3",
        },
        {
          id: 2,
          name: "Lean on",
          artistName: "Adam Levine",
          albumName: "Goind Down",
          year: 2001,
          src: "https://unsplash.com/photos/woman-in-black-tank-top-singing-on-stage-3-Kh6XSu9XQ",
          songSrc: "/audio/Ali_Gatie_What_If_I_Told_You_That_I_Love_You_.mp3",
        },
        {
          id: 3,
          name: "Counting Stars",
          artistName: "Adam Hart",
          albumName: "Spice It Up",
          year: 2013,
          src: "https://unsplash.com/photos/a-group-of-people-standing-around-a-dj-booth-GDdYMjRLuDE",
          songSrc: "/audio/Moh Moh Ke Dhaage (Female).mp3",
        },
      ],
    };
  },
};
</script>
