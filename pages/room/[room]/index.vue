<template>
    <v-container class="fill-height">
        <v-row>
            <v-col align="center">
                <v-card elevation="5" class="py-10 px-5" max-width="400">
                    <v-img v-if="track.cover" width="200" aspect-ratio="1" cover :src="track.cover" class="mb-4"></v-img>
                    <v-img v-else width="200" aspect-ratio="1" cover src="/img/cover-placeholder.jpg" class="mb-4"></v-img>

                    <v-card-title align="center" class="text-h4 font-weight-black mb-2">{{ track.title }}</v-card-title>
                    <v-card-subtitle align="center" class="text-subtitle-1 mb-6">{{ track.author }}</v-card-subtitle>

                    <v-card-text align="center">
                        <v-sheet class="d-flex justify-space-between">
                            <p>{{ secondsToString(currentTimestamp) }}</p>
                            <p>{{ secondsToString(track.duration) }}</p>
                        </v-sheet>
                        <v-slider v-model="currentTimestamp" :max="track.duration" @input="seekAudio"></v-slider>

                        <v-btn icon variant="outlined" @click="playPrevious()">
                            <v-icon>mdi-skip-previous</v-icon>
                        </v-btn>
                        <v-btn size="x-large" icon variant="outlined" @click="togglePlayPause" class="mx-6">
                            <v-icon v-if="isPlaying">mdi-pause</v-icon>
                            <v-icon v-else>mdi-play</v-icon>
                        </v-btn>
                        <v-btn icon variant="outlined" @click="playNext()">
                            <v-icon>mdi-skip-next</v-icon>
                        </v-btn>
                    </v-card-text>

                    <audio ref="audioPlayer" @timeupdate="updateTimestamp">
                        <source :src="track.src" type="audio/mpeg">
                    </audio>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>
  
<script setup>
// TODO: eat ass fix shit none of this bullshit works
const secondsToString = (seconds) => {
    return new Date(seconds * 1000)
        .toISOString()
        .slice(14, 19);
}

const track = ref({
    title: "C названием",
    author: "Известен",
    duration: 360,
    cover: "https://cdnn21.img.ria.ru/images/49873/01/498730163_0:177:2928:1824_1920x0_80_0_0_93fb227fb06f559b14009d1939cdf718.jpg",
    src: "https://radioulitka.ru/mount",
})

const audioPlayer = ref(null)
const isPlaying = ref(false)
const currentTimestamp = ref(0)


const playNext = () => {
    isPlaying.value = false;
}

const playPrevious = () => {
    isPlaying.value = false;
}

const togglePlayPause = () => {
    // send stop/pause state here
    if (audioPlayer.value.paused) {
        isPlaying.value = true;
        audioPlayer.value.play();
    } else {
        isPlaying.value = false;
        audioPlayer.value.pause();
    }
};

const updateTimestamp = () => {
    currentTimestamp.value = audioPlayer.value.currentTime;
};

const seekAudio = () => {
    // send new timestamp here
};

</script>
