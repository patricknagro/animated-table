<template>
  <v-card class="pa-2">
    <v-btn @click="add" class="mr-3">add</v-btn>
    <v-btn @click="remove" class="mr-3">remove</v-btn>
    <v-btn @click="change">change</v-btn>
    <v-data-table
      :items="items"
      :headers="headers"
      hide-default-footer
      :sort-by.sync="sortBy"
    >
      <template v-slot:body="{ items }">
        <tbody v-if="items.length" is="transition-group" name="row">
          <tr v-for="item in items" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.value }}</td>
          </tr>
        </tbody>
      </template>
    </v-data-table>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      sortBy: "value",
      headers: [
        {
          text: "id",
          value: "id",
          sortable: false
        },
        {
          text: "value",
          value: "value",
          sortable: true
        }
      ],
      items: [
        {
          id: 1,
          value: 10
        },
        {
          id: 2,
          value: 20
        },
        {
          id: 3,
          value: 30
        },
        {
          id: 4,
          value: 40
        },
        {
          id: 5,
          value: 50
        }
      ]
    };
  },
  methods: {
    add() {
      const newItem = {
        id: this.items.length + 1,
        value: Math.ceil(Math.random() * 100)
      };
      this.items.push(newItem);
    },
    remove() {
      this.items.pop();
    },
    change() {
      const qnt = this.items.length - 1;
      const index = Math.ceil(Math.random() * qnt);
      const itemsCopy = [...this.items];
      itemsCopy[index].value = Math.ceil(Math.random() * 100);
      this.items = itemsCopy;
    }
  }
};
</script>

<style>
#app {
  padding: 20px;
}
.row-enter-active,
.row-leave-active {
  transition: all 0.8s;
}
.row-enter,
.row-leave-to {
  opacity: 0;
  transform: translateY(100%);
}
.row-move {
  transition: transform 0.5s;
}
</style>
