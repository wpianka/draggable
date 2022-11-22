<script setup lang="ts">
import { ref } from "vue";
import draggable from "vuedraggable";

const enabled = ref(true);
const dragging = ref(false);
const list = ref([
  { id: 1, name: "Item 1" },
  { id: 2, name: "Item 2" },
  { id: 3, name: "Item 3" },
  { id: 4, name: "Item 4" },
]);

const checkMove = (e: any) => {
  console.log("Future index: " + e.draggedContext.futureIndex);
};
</script>

<template>
  <main>
    <section class="section">
      <div class="">
        <h1>Lista 1</h1>
        <draggable
          :list="list"
          :disabled="!enabled"
          item-key="name"
          class="list-group"
          ghost-class="ghost"
          :move="checkMove"
          @start="dragging = true"
          @end="dragging = false"
        >
          <template #item="{ element }">
            <div class="list-group-item" :class="{ 'not-draggable': !enabled }">
              {{ element.name }}
            </div>
          </template>
        </draggable>
      </div>
      <!-- <div>
        <h1>Lista 2</h1>
        <div class="wrapper"></div>
      </div> -->
    </section>
  </main>
</template>

<style scoped>
.section {
  outline: 1px solid #ccc;
  display: flex;
  width: 100%;
}

.list-group {
  padding: 1rem;
  margin: 1rem;
}

.list-group-item {
  border: 2px solid rgb(53, 5, 49);
  background-color: rgb(46, 32, 32);
  padding: 2rem;
  margin: 2rem;
  width: 600px;
  cursor: move;
}

.not-draggable {
  cursor: no-drop;
}
</style>
