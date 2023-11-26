<script setup>
import { useDisplay } from 'vuetify'
const { mobile } = useDisplay();

const mainDrawer = ref(!mobile.value);
const usersDrawer = ref(!mobile.value);

const props = defineProps({
    title: String,
    users: Array,
    links: Array
});
</script>

<template>
    <v-navigation-drawer v-model="mainDrawer" class="elevation-0" width="260">
        <v-list-item class="text-h4 my-4" align="center">
            <AppTitle />
        </v-list-item>

        <v-list-item min-height="48" v-for="link in links" :key="link.to" link :to="`/room/${link.to}`">
            <template v-slot:prepend>
                <v-icon :icon="link.icon"></v-icon>
            </template>
            <v-list-item-title>{{ link.title }}</v-list-item-title>
        </v-list-item>
    </v-navigation-drawer>

    <v-navigation-drawer location="right" v-model="usersDrawer" class="elevation-0" width="260">
        <v-list>
            <v-list-subheader>УЧАСТНИКИ — {{ users.length }}</v-list-subheader>
            <v-list-item v-for="user in users" :key="user.id" :prepend-avatar="user.avatar" :title="user.username"
                :subtitle="user.isHost ? 'Хост' : ''" class="mb-2"></v-list-item>
        </v-list>
    </v-navigation-drawer>

    <v-app-bar :elevation="0">
        <v-app-bar-nav-icon @click="mainDrawer = !mainDrawer"></v-app-bar-nav-icon>
        <v-row align="center">

            <v-col cols="4" align="left" class="d-none d-md-block">
                <v-toolbar-title v-if="!mainDrawer">
                    <AppTitle />
                </v-toolbar-title>
            </v-col>
            <v-col cols="4" align="center" class="d-none d-md-block">
                <v-toolbar-title>{{ title }}</v-toolbar-title>
            </v-col>

            <v-col cols="8" align="left" class="d-block d-md-none">
                <v-toolbar-title>{{ title }}</v-toolbar-title>
            </v-col>

            <v-col cols="4" align="right">
                <v-btn flat color="grey" @click="usersDrawer = !usersDrawer" class="mr-2 d-none d-md-block">
                    <span class="mr-2">СПИСОК УЧАСТНИКОВ</span>
                    <v-icon right>mdi-account-multiple</v-icon>
                </v-btn>
                <v-btn icon color="grey" @click="usersDrawer = !usersDrawer" class="mr-2 d-block d-md-none">
                    <v-icon right>mdi-account-multiple</v-icon>
                </v-btn>
            </v-col>
        </v-row>
    </v-app-bar>

    <v-main scrollable>
        <slot></slot>
    </v-main>
</template>