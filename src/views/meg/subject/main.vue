<script setup lang="ts">
import { ref } from 'vue'
import { ElTable } from 'element-plus'

interface Amplifier1 {
  Last_Name: string
  First_Name: string
  Date_Of_Birth: string
  Last_Recording: string
}

interface Amplifier2 {
  Recording_Date: string
  Recording_Length: string
  Segments: number
  Amplifier_Setup: string
  Sampling_Rate: number
  Total_Event_Count: number
  Total_Video_Count: number
  Notes: string
}
const currentRow = ref()
const singleTableRef = ref<InstanceType<typeof ElTable>>()

const setCurrent = (row?: Amplifier1) => {
  singleTableRef.value!.setCurrentRow(row)
}
const setCurren2 = (row?: Amplifier2) => {
  singleTableRef.value!.setCurrentRow(row)
}
const handleCurrentChange1 = (val: Amplifier1 | undefined) => {
  currentRow.value = val
}
const handleCurrentChange2 = (val: Amplifier2 | undefined) => {
  currentRow.value = val
}
const tableData1: Amplifier1[] = [
  {
    Last_Name: '张',
    First_Name: '三',
    Date_Of_Birth: '1972-12-23',
    Last_Recording: '2024-05-31 14-05-00',
  },
  {
    Last_Name: '李',
    First_Name: '四',
    Date_Of_Birth: '1999-02-27',
    Last_Recording: '2024-05-31 14-30-00',
  },
  {
    Last_Name: '王',
    First_Name: '五',
    Date_Of_Birth: '2000-04-30',
    Last_Recording: '2024-05-31 16-05-00',
  },
]

const tableData2: Amplifier2[] = [
  {
    Recording_Date: '2021-04-15 14-05-00',
    Recording_Length: '00:00:30',
    Segments: 1,
    Amplifier_Setup: 'EEG64-AUX-CA-208',
    Sampling_Rate: 500,
    Total_Event_Count: 0,
    Total_Video_Count: 0,
    Notes: '',
  },
  {
    Recording_Date: '2022-07-20 17-00-21',
    Recording_Length: '00:03:10',
    Segments: 1,
    Amplifier_Setup: 'EEG66-CA-208',
    Sampling_Rate: 500,
    Total_Event_Count: 0,
    Total_Video_Count: 0,
    Notes: '',
  },
  {
    Recording_Date: '2023-09-29 10-21-27',
    Recording_Length: '00:01:11',
    Segments: 2,
    Amplifier_Setup: 'EEG67-CA-208',
    Sampling_Rate: 500,
    Total_Event_Count: 0,
    Total_Video_Count: 0,
    Notes: '',
  },
  {
    Recording_Date: '2024-05-30 11-14-49',
    Recording_Length: '00:03:52',
    Segments: 1,
    Amplifier_Setup: 'EEG68-CA-208',
    Sampling_Rate: 500,
    Total_Event_Count: 0,
    Total_Video_Count: 0,
    Notes: '',
  },
]
</script>

<template>
  <el-tabs class="container" type="border-card">
    <el-tab-pane label="Subject and Recordings">
      <el-table ref="singleTableRef" :data="tableData1" highlight-current-row style="width: 100%; top: 0"
        @current-change="handleCurrentChange1"
      >
        <el-table-column prop="Last_Name" label="Last_Name"></el-table-column>
        <el-table-column prop="First_Name" label="First_Name"></el-table-column>
        <el-table-column prop="Date_Of_Birth" label="Date Of Birth"></el-table-column>
        <el-table-column prop="Last_Recording" label="Last Recording"></el-table-column>
        <el-table-column label="Others"></el-table-column>
      </el-table>
      <el-table
        ref="singleTableRef"
        :data="tableData2"
        highlight-current-row
        style="width: 100%"
        class="table2"
        @current-change="handleCurrentChange2"
      >
        <el-table-column prop="Recording_Date" label="记录日期"></el-table-column>
        <el-table-column prop="Recording_Length" label="记录时长"></el-table-column>
        <el-table-column prop="Segments" label="片段数量"></el-table-column>
        <el-table-column prop="Amplifier_Setup" label="Amplifier Setup"></el-table-column>
        <el-table-column prop="Sampling_Rate" label="Sampling Rate"></el-table-column>
        <el-table-column prop="Total_Event_Count" label="Total Event Count"></el-table-column>
        <el-table-column prop="Total_Video_Count" label="Total Video Count"></el-table-column>
        <el-table-column prop="Notes" label="Notes"></el-table-column>
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

.table2 {
  position: fixed;
  bottom: 200px;
}
</style>
