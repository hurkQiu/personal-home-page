<template>
  <a-table :dataSource="dataSource" :columns="columns" size="small" :pagination="false"></a-table>
</template>
<script>
import { Table } from 'ant-design-vue'
export default {
  data() {
    return {
      dataSource: [
        {
          key: '1',
          time: '8: 05 ~ 8: 55',
          mon: 'Computer Science',
          tue: '',
          wed: 'Computer Algorithm',
          thu: 'Computer Science',
          fri: ''
        },
        {
          key: '2',
          time: '9: 05 ~ 9: 55',
          mon: 'Computer Science',
          tue: 'Application Design',
          wed: 'Computer Algorithm',
          thu: 'Computer Science',
          fri: ''
        },
        {
          key: '3',
          time: '10: 05 ~ 10: 55',
          mon: 'Computer Science',
          tue: 'Application Design',
          wed: 'Computer Algorithm',
          thu: 'Computer Science',
          fri: ''
        },
        {
          key: '4',
          time: '11: 05 ~ 11: 55',
          mon: '',
          tue: '',
          wed: '',
          thu: '',
          fri: ''
        },
        {
          key: '5',
          time: '12: 00 ~ 13: 00',
          mon: 'lunch',
          tue: 'lunch',
          wed: 'lunch',
          thu: 'lunch',
          fri: 'lunch'
        },
        {
          key: '6',
          time: '13: 10 ~ 14: 00',
          mon: '',
          tue: '',
          wed: '10 Downing Street',
          thu: 'Application Design',
          fri: ''
        },
        {
          key: '7',
          time: '14: 10 ~ 15: 00',
          mon: 'calculus',
          tue: '',
          wed: '10 Downing Street',
          thu: 'Application Design',
          fri: 'calculus'
        },
        {
          key: '8',
          time: '15: 10 ~ 16: 00',
          mon: 'calculus',
          tue: '',
          wed: '10 Downing Street',
          thu: 'Application Design',
          fri: 'calculus'
        },
        {
          key: '9',
          time: '16: 10 ~ 17: 00',
          mon: 'calculus',
          tue: '',
          wed: '10 Downing Street',
          thu: '',
          fri: 'calculus'
        }
      ],

      columns: [
        {
          title: '',
          dataIndex: 'time',
          key: 'time',
          width: '10%',
          ellipsis: true
        },
        {
          title: 'Mon',
          dataIndex: 'mon',
          key: 'mon',
          width: '10%',
          ellipsis: true
        },
        {
          title: 'Tue',
          dataIndex: 'tue',
          key: 'tue',
          width: '10%',
          ellipsis: true
        },
        {
          title: 'Wed',
          dataIndex: 'wed',
          key: 'wed',
          width: '10%',
          ellipsis: true
        },
        {
          title: 'Thu',
          dataIndex: 'thu',
          key: 'thu',
          width: '10%',
          ellipsis: true
        },
        {
          title: 'Fri',
          dataIndex: 'fri',
          key: 'fri',
          width: '10%',
          ellipsis: true
        }
      ]
    }
  },
  components: {
    ATable: Table
  }
}
</script>
<style></style>
