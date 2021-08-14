<template>
  <div id="group" class="card shadow p-3 mb-5 bg-white rounded">
    <div class="card-body">
      <h6 class="card-title">{{ groupData.name }}</h6>
      <div id="color-box">
        <template v-for="(color, index) in colors" :key="index">
          <span
            class="dot"
            :style="{
              'background-color': `rgb(${color.r},${color.g},${color.b})`,
            }"
          ></span>
        </template>
      </div>
    </div>
    <div class="btn-group" style="width: 20px; height: 28px">
      <button
        id="btnGroupDrop"
        type="button"
        class="btn btn-sm dropdown-toggle"
        data-bs-toggle="dropdown"
        aria-expanded="false"
      ></button>
      <ul class="dropdown-menu" aria-labelledby="btnGroupDrop">
        <li><a class="dropdown-item">edit</a></li>
        <li><a class="dropdown-item" style="color: red">delete</a></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: ["groupData"],
  data() {
    return {};
  },
  computed: {
    colors: function () {
      if (!this.groupData) {
        return [];
      }
      let size = Math.min(this.groupData.colors.length, 14);
      return this.groupData.colors.slice(0, size);
    },
  },
  methods: {},
};
</script>

<style>
#group {
  margin: 10px;
  height: 150px;
  width: 320px;
  display: flex;
  flex-direction: row;
}
#color-box {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
.dot {
  height: 25px;
  width: 25px;
  border-radius: 50%;
  display: inline-block;
  margin: 3px;
}
</style>