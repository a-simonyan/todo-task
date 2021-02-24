<template>
  <div class="col-4 mx-auto">
    <form @submit.prevent="addToDo">
      <div class="mb-3 ">
        <label for="name" class="form-label">Name</label>
        <input
          type="text"
          class="form-control"
          id="name"
          v-model="toDoItems.name"
          placeholder="Name"
        />
      </div>
      <div class="mb-3">
        <label for="description" class="form-label">Description</label>
        <input
          type="text"
          class="form-control"
          id="description"
          v-model="toDoItems.description"
          placeholder="Description"
        />
      </div>

      <div class="mb-3">
        <label for="workload" class="form-label">Workload</label>
        <input
          type="date"
          class="form-control"
          id="workload"
          v-model="toDoItems.workload"
          placeholder="Workload"
        />
      </div>
      <button class="btn btn-primary d-block ml-auto">Add ToDo</button>
    </form>

    <div v-if="items.length">
      <table class="table mt-5">
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">Description</th>
            <th scope="col">Workload</th>
            <th scope="col">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in items" :key="item.id">
            <th scope="row">{{ item.name }}</th>
            <td>
              <p
                :class="{ ellipsis: isVisible }"
                @click="showDescription(item)"
              >
                {{ item.description }}
              </p>
            </td>
            <td>{{ item.workload }}</td>
            <th
              scope="col"
              class="btn btn-danger btn-sm"
              @click="removeItem(item.id)"
            >
              remove
            </th>
          </tr>
        </tbody>
      </table>
    </div>
    <div v-else>
      <h3>You have not any items yet.</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "todo",
  data() {
    return {
      toDoItems: {
        id: 0,
        name: "",
        description: "",
        workload: "",
      },
      items: [],
      isVisible: true,
    };
  },
  methods: {
    addToDo() {
      const { name, description, workload } = this.toDoItems;

      if (name && description && workload !== "") {
        const newToDo = {
          id: Date.now(),
          name: name,
          description: description,
          workload: workload,
        };
        this.items.push(newToDo);
        this.toDoItems.name = "";
        this.toDoItems.description = "";
        this.toDoItems.workload = "";
      } else {
        alert("Fill in all fields please");
      }
    },

    removeItem(id) {
      this.items = this.items.filter((i) => i.id !== id);
    },
    showDescription(item) {
      alert(item.description);
    },
  },
};
</script>

<style>
.ellipsis {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  width: 200px;
}
</style>
