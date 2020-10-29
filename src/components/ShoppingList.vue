<template>
    <v-card
        class="mx-auto"
        max-width="344"
      >
        <v-list dense class="body">
            <v-text-field
                label="Text"
                outlined
                ></v-text-field>
            <v-chip
                class="ma-2"
                color="pink"
                label
                text-color="white"
                >
                Order
                <v-icon>mdi-menu-down</v-icon>
                <v-icon>mdi-menu-up</v-icon>
            </v-chip>
            <v-list-item-group
                v-model="selectedItem"
                color="primary"
            >
                <v-list-item
                    v-for="(item, i) in items"
                    :key="i"
                    draggable="true" 
                    ondragstart="dragstartHandler(event)">
                <v-list-item-content>
                    <v-list-item-title v-text="item"></v-list-item-title>
                </v-list-item-content>
                </v-list-item>
            </v-list-item-group>
        </v-list>
    </v-card>
</template>

<script>
  export default {
    props: {
        items: Array
    },
    data: () => ({
      selectedItem: 1,
    }),
    methods: {
        dragstartHandler(event) {
            event.dataTransfer.setData("text/plain", event.target.id);
        }
    }
  }
</script>

<style>
    .body {
        padding: 10px!important;
    }
</style>
