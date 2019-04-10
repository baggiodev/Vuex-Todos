<template>
  <!-- Modal -->
  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    role="dialog"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">Edit the title</h5>
          <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body">
          <input type="text" v-model="title" id="modTitle">
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
          <button type="button" class="btn btn-green" @click="modalClicked">Save changes</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  name: "Modal",
  data() {
    return {
      id: "",
      title: "",
      completed: ""
    };
  },
  methods: {
    ...mapActions(["updateTodo"]),
    modalClicked() {
      const updTodo = {
        id: this.id,
        title: this.title,
        completed: this.completed
      };
      this.updateTodo(updTodo);
      // eslint-disable-next-line
      $(this.$el).modal("hide");
    }
  }
};
</script>

<style>
.btn-green {
  background: #41b883;
}
</style>
