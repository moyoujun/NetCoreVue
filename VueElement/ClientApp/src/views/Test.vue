<template>
  <div class="test">
    <el-container>
      <el-header>Header</el-header>
      <el-main>
        <el-button type="primary" v-on:click="greet">主要按钮</el-button>
        <div>
          <el-table :data="items" style="width: 80%; margin:0 auto">
            <el-table-column prop="date" label="日期" width="auto">
            </el-table-column>
            <el-table-column prop="temperatureC" label="温度℃" width="180">
            </el-table-column>
            <el-table-column prop="temperatureF" label="温度℉" width="180">
            </el-table-column>
            <el-table-column prop="summary" label="详情"> </el-table-column>
          </el-table>
        </div>
      </el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: "Test",
  components: {},
  data() {
    return {
      items: [],
    };
  },

  methods: {
    greet: function(event) {
      this.axios.get("/WeatherForecast").then((response) => {
        this.items = response.data;
      });
    },
  },
};
</script>
