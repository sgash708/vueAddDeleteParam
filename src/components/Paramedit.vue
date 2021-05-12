<template>
  <form id="form">
    <table border="1">
      <tr v-for="(sec, index) in task['params']" :key="index">
        <td>Name</td>
        <td><input v-model="sec.Name" /></td>
        <td>Path</td>
        <td><input v-model="sec.ValueFrom" /></td>
        <td><button @click.prevent="deleteParam(index)">削除</button></td>
      </tr>
    </table>
    <a @click.prevent="addParam">環境変数の追加</a>
  </form>
</template>

<script>
export default {
  data() {
    return {
      // 更新対象
      task: {
        params: [
          { Name: "test1", ValueFrom: "test/path/1" },
          { Name: "test2", ValueFrom: "test/path/2" },
        ],
      },
      addForm: { Name: "", ValueFrom: "" },
    };
  },
  created() {},
  methods: {
    deleteParam: function (id) {
      let self = this;
      self.task.params.splice(id, 1);
    },
    addParam: function () {
      let self = this;
      self.task.params.push(self.addForm);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
