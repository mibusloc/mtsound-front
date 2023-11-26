<template>
    <RoomLayout :title="roomTitle" :users="users" :links="links">
        <NuxtPage :users="users" :currentUserId="currentUserId" />
    </RoomLayout>
</template>

<script setup>
const roomTitle = ref("Золотой Унитаз");

const roomId = "balls123"

const links = [
    { title: 'Плеер', icon: 'mdi-play-box', to: `${roomId}/` },
    { title: 'Чат комнаты', icon: 'mdi-chat', to: `${roomId}/chat` },
    { title: 'Очередь медиа', icon: 'mdi-playlist-music', to: `${roomId}/queue` },
]

const currentUserId = ref(0);

const users = [
    { username: 'Host user', avatar: "https://i.imgur.com/7jfITY5.jpg", isHost: true, id: 0 },
    { username: 'Second user', avatar: "https://i.imgur.com/7jfITY5.jpg", isHost: false, id: 1 },
    { username: 'Third user', avatar: "https://i.imgur.com/7jfITY5.jpg", isHost: false, id: 2 },
]
</script>