<template>
  <div id="filter"></div>
  <div id="box">
    <div id="dialog" class="card shadow p-3 mb-5 bg-white rounded">
      <div class="card-body">
        <form>
          <div class="mb-3">
            <label for="groupName" class="form-label">Group Name</label>
            <input
              v-model="groupData.name"
              type="text"
              class="form-control"
              id="groupName"
            />
          </div>
        </form>
        <div>
          <button @click="save" type="button" class="btn btn-outline-primary">
            Save
          </button>
          <button @click="close" type="button" class="btn btn-outline-primary">
            Cancel
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["groupDialogData"],
  emits: ["closeDialog", "saveGroup"],
  data() {
    return {
      groupData: this.groupDialogData,
    };
  },
  methods: {
    close() {
      this.$emit("closeDialog");
    },
    save() {
      if (!this.groupData.name) {
        alert("Group 名稱不能為空");
        return;
      }
      this.$emit("saveGroup", this.groupData);
      this.close();
    },
  },
};
</script>

<style>
#filter {
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
  background-color: black;
  opacity: 20%;
}
#box {
  position: absolute;
  left: 0;
  top: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  z-index: 1;
  height: 100%;
  width: 100%;
}
#dialog {
  align-self: center;
  z-index: 2;
  background: white;
  height: 200px;
  width: 400px;
}
button {
  margin-right: 5px;
}
</style>