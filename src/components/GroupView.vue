<template>
  <div id="group-box">
    <template v-for="group in groupList" :key="group.id">
      <group-card :groupData="group"></group-card>
    </template>
  </div>
  <button
    id="add_button"
    @click="openGroupDialog(null)"
    type="button"
    class="btn btn-danger btn-circle btn-md"
  >
    +
  </button>
  <group-dialog
    :groupDialogData="groupDialogData"
    @close-dialog="closeGroupDialog"
    @save-group="saveGroup"
    v-if="isGroupDialogActive"
  ></group-dialog>
</template>

<script>
import GroupDialog from "../components/GroupDialog.vue";
import GroupCard from "../components/GroupCard.vue";
export default {
  components: {
    GroupDialog,
    GroupCard,
  },
  data() {
    return {
      isGroupDialogActive: false,
      groupDialogData: { name: "", colors: [] },
      groupList: [],
    };
  },
  mounted() {
    this.refresh();
  },
  methods: {
    openGroupDialog(groupName) {
      this.groupDialogData.name = groupName;
      this.isGroupDialogActive = true;
    },
    closeGroupDialog() {
      this.isGroupDialogActive = false;
    },
    saveGroup(groupDialogData) {
      this.axios
        .post("http://localhost:3000/color_groups", groupDialogData)
        .finally(() => {
          this.refresh();
        });
    },
    refresh() {
      this.axios.get("http://localhost:3000/color_groups").then((res) => {
        this.groupList = res.data;
      });
    },
  },
};
</script>

<style>
#group-box {
  display: flex;
  justify-content: row;
  flex-wrap: wrap;
  margin-right: 80px;
}

#add_button {
  position: absolute;
  right: 15px;
  bottom: 15px;
  width: 70px;
  height: 70px;
  padding: 10px 16px;
  border-radius: 35px;
  font-size: 28px;
  text-align: center;
}
</style>