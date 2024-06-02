<script setup lang="ts">
import { ref } from 'vue'
import { ElTable } from 'element-plus'

interface Montage {
  name: string
  totalCount: number
  refCount: number
  BIPCount: number
  sensorCount: number
  readOnly: boolean
  default: string
  aquire: boolean
  review: boolean
}

const currentRow = ref()
const singleTableRef = ref<InstanceType<typeof ElTable>>()

const setCurrent = (row?: Montage) => {
  singleTableRef.value!.setCurrentRow(row)
}
const handleCurrentChange = (val: Montage | undefined) => {
  currentRow.value = val
}
const tableData: Montage[] = [
  {
    name: 'Item 1',
    totalCount: 10,
    refCount: 5,
    BIPCount: 3,
    sensorCount: 2,
    readOnly: true,
    default: 'default 1',
    aquire: true,
    review: true,
  },
  {
    name: 'Item 2',
    totalCount: 20,
    refCount: 10,
    BIPCount: 6,
    sensorCount: 4,
    readOnly: false,
    default: 'default 2',
    aquire: true,
    review: true,
  },
  {
    name: 'Item 3',
    totalCount: 30,
    refCount: 15,
    BIPCount: 9,
    sensorCount: 6,
    readOnly: true,
    default: 'default 3',
    aquire: false,
    review: false,
  },
  {
    name: 'Item 4',
    totalCount: 40,
    refCount: 20,
    BIPCount: 12,
    sensorCount: 8,
    readOnly: false,
    default: 'default 4',
    aquire: true,
    review: true,
  },
  {
    name: 'Item 5',
    totalCount: 50,
    refCount: 25,
    BIPCount: 15,
    sensorCount: 10,
    readOnly: true,
    default: 'default 5',
    aquire: false,
    review: false,
  },
  {
    name: 'Item 3',
    totalCount: 30,
    refCount: 15,
    BIPCount: 9,
    sensorCount: 6,
    readOnly: true,
    default: 'default 3',
    aquire: false,
    review: false,
  },
  {
    name: 'Item 4',
    totalCount: 40,
    refCount: 20,
    BIPCount: 12,
    sensorCount: 8,
    readOnly: false,
    default: 'default 4',
    aquire: true,
    review: true,
  },
]

</script>

<template>
  <el-tabs class="container" type="border-card">
    <el-tab-pane label="User">
      <el-table ref="singleTableRef" :data="tableData" highlight-current-row style="width: 100%"
        @current-change="handleCurrentChange">
        <el-table-column prop="name" label="Name"></el-table-column>
        <el-table-column prop="totalCount" label="Total Count"></el-table-column>
        <el-table-column prop="refCount" label="Ref Count"></el-table-column>
        <el-table-column prop="BIPCount" label="BIP Count"></el-table-column>
        <el-table-column prop="sensorCount" label="Sensor Count"></el-table-column>
        <el-table-column prop="readOnly" label="Read Only"></el-table-column>
        <el-table-column prop="default" label="Default"></el-table-column>
        <el-table-column prop="aquire" label="Aquire"></el-table-column>
        <el-table-column prop="review" label="Review"></el-table-column>
      </el-table>
    </el-tab-pane>
  </el-tabs>
</template>

<style scoped lang="scss">
.container {
  height: 100%;
  width: 100%;
}

.el-table-column {
  text-align: center;
}
</style>
