<script setup lang="ts">
const route = useRoute()
</script>

<template>
  <v-container class="fill-height">
    <v-row>
      <v-col align="center">
        <v-sheet max-width="500px" class="pa-5">

          <v-container>
            <v-row>
              <v-col>
                <h1 class="text-h3"><AppTitle /></h1>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <v-btn color="primary" block to="/login" flat height="60">Войти</v-btn>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <v-btn color="secondary" block to="/registration" flat>Регистрация</v-btn>
              </v-col>
            </v-row>

            <v-row>
              <v-col>
                <v-btn color="warning" block to="/room/whatever/chat" flat>похуй на регистрацию</v-btn>
              </v-col>
            </v-row>
          </v-container>

        </v-sheet>
      </v-col>
    </v-row>
  </v-container>
</template>
