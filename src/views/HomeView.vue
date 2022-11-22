<script setup lang="ts">
import { ref } from "vue";
import draggable from "vuedraggable";

const list1 = ref([
  { id: 1, name: "Item 1" },
  { id: 2, name: "Item 2" },
  { id: 3, name: "Item 3" },
  { id: 4, name: "Item 4" },
]);

const list2 = ref([
  { id: 5, name: "Item 5" },
  { id: 6, name: "Item 6" },
  { id: 7, name: "Item 7" },
]);

const log = (evt: any) => {
  console.log(evt);
};

const clone = (el) => {
  el.name + " cloned";
};
</script>

<template>
  <main>
    <section class="section">
      <div class="wrapper">
        <h3>Draggable 1</h3>
        <draggable
          :list="list1"
          item-key="name"
          class="list-group"
          @change="log"
          group="people"
        >
          <template #item="{ element, index }">
            <div class="list-group-item">{{ element.name }} {{ index }}</div>
          </template>
        </draggable>
      </div>
      <div class="wrapper">
        <h3>Draggable 2</h3>
        <draggable
          :list="list2"
          item-key="name"
          class="list-group"
          @change="log"
          group="people"
        >
          <template #item="{ element, index }">
            <div class="list-group-item">{{ element.name }} {{ index }}</div>
          </template>
        </draggable>
      </div>
    </section>
  </main>
</template>

<style scoped>
.section {
  outline: 1px solid #ccc;
  display: flex;
  width: 800px;
}

.list-group {
  padding: 1rem;
  margin: 1rem;
}

.list-group-item {
  border: 2px solid rgb(53, 5, 49);
  background-color: rgb(46, 32, 32);
  padding: 2rem;
  width: 100%;
  cursor: move;
}

.not-draggable {
  cursor: no-drop;
}
</style>
