<template>
    <v-container class="fill-height">
        <v-row>
            <v-col align="center">
                <v-sheet max-width="500px" class="pt-5">
                    <h1>Регистрация</h1>
                    <v-form fast-fail class="pa-5">
                        <v-text-field v-model="username" label="Имя" :rules="usernameRules"></v-text-field>

                        <v-text-field v-model="password" label="Пароль" :rules="passwordRules"
                            type="password"></v-text-field>

                        <v-text-field v-model="passwordConfirm" label="Повторите пароль" :rules="passwordConfirmRules"
                            type="password"></v-text-field>

                        <v-btn type="submit" color="primary" class="mt-2">Зарегистрироваться</v-btn>
                    </v-form>
                </v-sheet>
            </v-col>
        </v-row>
    </v-container>
</template>
  
<script setup>
const username = ref('')
const usernameRules = [
    v => {
        if (v?.length > 2) return true
        return 'Имя должно содержать минимум 2 символа.'
    },
]

const password = ref('')
const passwordRules = [
    v => !!v || "Требуется пароль."
];

const passwordConfirm = ref('')
const passwordConfirmRules = [
    v => !!v || "Требуется подтверждение пароля.",
    v => v == password.value || "Пароли не совпадают."
];
</script>