<template>
    <v-container>
        <v-row>
            <v-col align="center">
                <v-virtual-scroll ref="msgScroll" :items="messages" max-width="800">

                    <template v-slot:default="{ item }">
                        <ChatMessage :isCurrentUser="item.userId === useAttrs().currentUserId"
                            :user="useAttrs().users.find(user => user.id === item.userId)">
                            {{ item.text }}
                        </ChatMessage>
                    </template>

                </v-virtual-scroll>
            </v-col>
        </v-row>
    </v-container>

    

    <v-footer app height="72" class="d-flex justify-center">
        <v-responsive max-width="840">
            <v-form class="d-flex align-center w-100">
                <v-text-field bg-color="" class="overflow-hidden mr-1" placeholder="Написать сообщение" density="compact"
                    flat hide-details rounded="lg" variant="solo-filled" autocomplete="off"></v-text-field>
                <v-btn flat icon>
                    <v-icon>mdi-send</v-icon>
                </v-btn>
            </v-form>
        </v-responsive>
    </v-footer>
</template>

<script setup>


const msgScroll = ref(null);

const messages = [
    { userId: 0, text: "Привет, как дела?", id: 0 },
    { userId: 1, text: "Привет! Всё отлично, спасибо.", id: 1 },
    { userId: 2, text: "Привет, ребята! Что нового?", id: 2 },
    { userId: 0, text: "Не много занят, но в целом нормально.", id: 3 },
    { userId: 1, text: "Понятно. У меня тоже много дел.", id: 4 },
    { userId: 2, text: "Давайте встретимся на выходных?", id: 5 },
    { userId: 0, text: "К сожалению, у меня уже есть планы.", id: 6 },
    { userId: 1, text: "Может быть в следующий раз.", id: 7 },
    { userId: 2, text: "Хорошо, давайте организуем что-то потом.", id: 8 },
    { userId: 0, text: "Как вам такая идея: посетить новый ресторан?", id: 9 },
    { userId: 1, text: "Отличная идея! Как называется ресторан?", id: 10 },
    { userId: 2, text: "Я слышал, там прекрасная кухня. Давайте попробуем.", id: 11 },
    { userId: 0, text: "Хорошо, договорились на завтра в 19:00?", id: 12 },
    { userId: 1, text: "Вполне подходит. Увидимся завтра!", id: 13 },
    { userId: 2, text: "Отлично, жду вас! Будет весело.", id: 14 },
    { userId: 0, text: "Извините, что не могу присоединиться. У меня другие планы.", id: 15 },
    { userId: 1, text: "Ничего страшного, может в следующий раз.", id: 16 },
    { userId: 2, text: "Будет ещё много возможностей. Удачи вам!", id: 17 },
    { userId: 0, text: "Сегодня такая плохая погода...", id: 18 },
    { userId: 1, text: "Да, дождь довольно сильный. Лучше оставайтесь дома.", id: 19 },
    { userId: 2, text: "Мне нравится звук дождя. Это такой уютный вечер.", id: 20 },
    { userId: 0, text: "Да, но завтра снова будет солнечно.", id: 21 },
    { userId: 1, text: "Отлично, пойду гулять завтра.", id: 22 },
    { userId: 2, text: "Давайте соберёмся и проведём время на свежем воздухе.", id: 23 },
    { userId: 0, text: "Отличная идея! Может быть, пикник в парке?", id: 24 },
    { userId: 1, text: "Звучит замечательно. Я принесу закуски.", id: 25 },
    { userId: 2, text: "А я возьму с собой игры. Будет весело!", id: 26 },
    { userId: 0, text: "Отлично, давайте встретимся у входа в парк в 12:00.", id: 27 },
    { userId: 1, text: "До встречи завтра! Будет весело!", id: 28 },
    { userId: 2, text: "Не могу дождаться. Увидимся!", id: 29 },
    { userId: 0, text: "Привет, как прошёл ваш день?", id: 30 },
    { userId: 1, text: "Прекрасно! Сделал много дел и даже нашёл время для отдыха.", id: 31 },
    { userId: 2, text: "У меня тоже всё отлично. Спасибо, что спросил!", id: 32 },
    { userId: 0, text: "Рад слышать, что у вас обоих всё хорошо.", id: 33 },
    { userId: 1, text: "А у тебя как дела? Есть какие-то новости?", id: 34 },
    { userId: 2, text: "Ничего особенного. Просто тихий вечер.", id: 35 },
    { userId: 0, text: "Понятно. Наверное, пора отдохнуть после такого дня.", id: 36 },
    { userId: 1, text: "Да, согласен. Хорошего вечера, ребята!", id: 37 },
    { userId: 2, text: "Вам тоже хорошего вечера! Увидимся завтра.", id: 38 },
    { userId: 0, text: "Привет! Как прошла встреча в ресторане?", id: 39 },
    { userId: 1, text: "Было замечательно! Еда была вкусной, а атмосфера приятная.", id: 40 },
    { userId: 2, text: "Рад, что вам понравилось. Давайте ещё раз встретимся где-нибудь.", id: 41 },
    { userId: 0, text: "Да, я был бы за! Может быть, следующий раз выберем что-то новенькое?", id: 42 },
    { userId: 1, text: "Отличная идея! Давайте искать интересные места в городе.", id: 43 },
    { userId: 2, text: "Звучит как план! Дайте знать, когда будете свободны.", id: 44 },
    { userId: 0, text: "Договорились! Увидимся скоро.", id: 45 },
    { userId: 1, text: "До встречи! Будет весело провести время.", id: 46 },
    { userId: 2, text: "Жду с нетерпением! До скорой встречи.", id: 47 },
    { userId: 0, text: "Привет! Как ваши выходные прошли?", id: 48 },
    { userId: 1, text: "Отлично! Я провёл время с семьёй и отдохнул.", id: 49 },
];
</script>