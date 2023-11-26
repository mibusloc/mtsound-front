<script setup>
const props = defineProps({
    isCurrentUser: Boolean,
    user: Object
});
</script>

<template>
    <v-container>
        <v-row :justify="isCurrentUser ? 'end' : 'start'">
            <v-card max-width="400" :align="isCurrentUser ? 'right' : 'left'"
                :class="`mb-2 text-grey-lighten-2 ${isCurrentUser ? 'ml-5 pl-2' : 'mr-5 pr-2'}`"
                :variant="isCurrentUser ? 'tonal' : 'flat'">

                <v-card-item :append-avatar="user.avatar" v-if="isCurrentUser">
                    <v-card-title class="text-subtitle-1 font-weight-bold">
                        {{ user.username }}
                    </v-card-title>
                </v-card-item>
                <v-card-item :prepend-avatar="user.avatar" v-else>
                    <v-card-title class="text-subtitle-1 font-weight-bold">
                        {{ user.username }}
                    </v-card-title>
                </v-card-item>

                <v-card-text class="text-body-1">
                    <slot></slot>
                </v-card-text>
            </v-card>
        </v-row>
    </v-container>
</template>