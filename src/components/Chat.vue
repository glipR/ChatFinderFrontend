<template>
    <v-dialog
        transition="dialog-bottom-transition"
        max-width="600"
    >
    <template v-slot:activator="dialog">
        <v-list-item @click="dialog.value = true">
            <v-list-item-avatar>
                <v-icon
                    class="grey lighten=1"
                    dark
                >
                    {{ chat.group_type == 'discord' ? 'mdi-discord' : (chat.group_type == "facebook" ? 'mdi-facebook' : 'mdi-help-circle') }}
                </v-icon>
            </v-list-item-avatar>
            <v-list-item-content style="text-align: left">
                <v-list-item-title v-text="chat.show_name"></v-list-item-title>
                <v-list-item-subtitle v-text="`${chat.year}`"></v-list-item-subtitle>
            </v-list-item-content>
        </v-list-item>
    </template>
    <template v-slot:default="dialog">
        <v-card>
            <v-card-title>
            {{ chat.show_name }}
            </v-card-title>
            <v-card-text v-show="chat.group_type == 'discord'">
                Click the link below to join the Discord server.<br>
                <a target="_blank" :href="chat.group_link">{{chat.group_link}}</a>
            </v-card-text>
            <v-card-text v-show="chat.group_type == 'facebook'">
                Click the link below to join the Facebook group chat.<br>
                <a target="_blank" :href="chat.group_link">{{chat.group_link}}</a>
            </v-card-text>
            <v-card-text v-show="chat.group_type == 'facebook'">
                Click the link below to join the group.<br>
                <a target="_blank" :href="chat.group_link">{{chat.group_link}}</a>
            </v-card-text>
            <v-card-actions class="justify-end">
                <v-btn
                    text
                    @click="dialog.value = false"
                >Close</v-btn>
            </v-card-actions>
        </v-card>
    </template>
    </v-dialog>
</template>
<script>
export default {
    props: ['chat'],
}
</script>
