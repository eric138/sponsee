<template>
  <a-row type="flex" justify="space-between">
    <a-col :span="12">col-12</a-col>
    <a-col :span="12">col-12</a-col>
  </a-row>
  <a-row type="flex" justify="space-between">
    <a-col :span="8">col-8</a-col>
    <a-col :span="8">col-8</a-col>
    <a-col :span="8">col-8</a-col>
  </a-row>
  <a-row type="flex" justify="space-between">
    <a-col :span="6">col-6</a-col>
    <a-col :span="4">col-4</a-col>
    <a-col :span="4">col-4</a-col>
    <a-col :span="6">col-6</a-col>
  </a-row>
</template>

<style scoped lang="scss">
.ant-row {
  border: 1px solid black;
  max-width: 80%;
  margin-left: auto;
  margin-right: auto;
  padding: 3px;
  box-shadow: 4px 4px 8px 1px rgba(2, 2, 32, 0.315);
}
.ant-row + .ant-row {
  margin-top: 24px;
}
.ant-col {
  border: 1px solid white;
  background-color: burlywood;
}
.ant-col + .ant-col + .ant-col {
  color: blue;
}
</style>
