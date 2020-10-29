<template>
<v-app>
  <v-main>
    <div class="row">
      <div class="col-3">
        <v-card
          class="mx-auto"
          max-width="300"
          tile>
          <v-text-field
            label="Text"
            outlined
            v-model="text1"
          ></v-text-field>
          <v-list nav dense>
            <v-list-item-group
              color="primary">
              <draggable class="list-group" :list="list1" group="people">
                <v-list-item
                  v-for="(element) in list1"
                  :key="element.id"
                >
                  {{ element.name }} {{ element.id }}
                </v-list-item>
              </draggable>
            </v-list-item-group>
          </v-list>
        </v-card>
      </div>

      <div class="col-3">
        <v-card
          class="mx-auto"
          max-width="300"
          tile>
          <v-text-field
            label="Text"
            outlined
            v-model="text2"
          ></v-text-field>
          <v-list nav dense>
            <v-list-item-group
              color="primary">
              <draggable class="list-group" :list="list2" group="people">
                <v-list-item
                  class="list-group-item"
                  v-for="(element) in list2"
                  :key="element.id"
                >
                  {{ element.name }} {{ element.id }}
                </v-list-item>
              </draggable>
            </v-list-item-group>
          </v-list>
        </v-card>
      </div>
      <div class="col-3">
        <v-btn
          class="mx-2"
          fab
          dark
          large
          color="error"
          @click="addText"
        >
          <v-icon dark>
            mdi-plus
          </v-icon>
        </v-btn>
      </div>

      <rawDisplayer class="col-3" :value="list1" title="List 1" />

      <rawDisplayer class="col-3" :value="list2" title="List 2" />
    </div>
  </v-main>
</v-app>
</template>
<script>
import draggable from 'vuedraggable'
export default {
  name: "two-lists",
  display: "Two Lists",
  order: 1,
  components: {
    draggable
  },
  data() {
    return {
      list1: [
        { name: "John", id: 1 },
        { name: "Joao", id: 2 },
        { name: "Jean", id: 3 },
        { name: "Gerard", id: 4 }
      ],
      list2: [
        { name: "Juan", id: 5 },
        { name: "Edgard", id: 6 },
        { name: "Johnson", id: 7 }
      ],
      text1: '',
      text2: ''
    };
  },
  methods: {
    addText() {
      const id = this.list1.length + this.list2.length + 1;
      if (this.text1 != ''){
        this.list1.push({ name: this.text1, id: id });
        this.text1 = '';
      }
      if (this.text2 != ''){
        this.list2.push({ name: this.text2, id: this.text2text1 != ' ' ? id + 1 : id });
        this.text2 = '';
      }
    }
  }
};
</script>