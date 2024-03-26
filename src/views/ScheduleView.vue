<template>
  <div class="content">
    <div class="calendar-content">
      <Calendar v-model:value="value">
        <template #dateCellRender="{ current: value }">
          <ul class="events">
            <li v-for="item in getListData(value)" :key="item.content">
              <Badge :status="item.type" :text="item.content" />
            </li>
          </ul>
        </template>
        <template #monthCellRender="{ current: value }">
          <div v-if="getMonthData(value)" class="notes-month">
            <section>{{ getMonthData(value) }}</section>
          </div>
        </template>
      </Calendar>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
import { Calendar, Badge } from 'ant-design-vue'

const value = ref<any>()

const getListData = (value: any) => {
  let listData: { type: any; content: string }[] = []
  switch (value.day()) {
    case 1:
      listData = [{ type: 'warning', content: 'Calculus quiz.' }]
      break
    case 3:
      listData = [{ type: 'warning', content: 'Algorithm quiz' }]
      break
    default:
  }
  return listData
}

const getMonthData = (value: any) => {
  if (value.month() === 8) {
    return 'test test test'
  }
}
</script>
<style scoped>
.content {
  display: flex;
  background-color: rgb(255, 255, 255);
  overflow: auto;
}
.calendar-content {
  position: relative;
  left: 5%;
  width: 90%;
  height: 90%;
}
.events {
  list-style: none;
  margin: 0;
  padding: 0;
}
.events .ant-badge-status {
  overflow: hidden;
  white-space: nowrap;
  width: 100%;
  text-overflow: ellipsis;
  font-size: 12px;
}
.notes-month {
  text-align: center;
  font-size: 28px;
}
.notes-month section {
  font-size: 28px;
}
</style>
