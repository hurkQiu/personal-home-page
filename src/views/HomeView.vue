<template>
  <div class="content">
    <div></div>
    <div class="second-row">
      <div class="announcement">
        <div class="title">Announcement</div>
        <div class="announce-item">
          <div>Course Selection Notice</div>
          <div>9/1</div>
        </div>
        <div class="announce-item">
          <div>Tuition and Fees</div>
          <div>8/30</div>
        </div>
        <div class="announce-item">
          <div>Course Information System & Course Selection System</div>
          <div>8/25</div>
        </div>
      </div>
      <div></div>
      <div class="schedule">
        <div class="title">Schedule</div>
        <a-calendar :fullscreen="false"> </a-calendar>
      </div>
    </div>
    <div class="third-row">
      <div class="credit">
        <div class="title">Credit</div>
        <div class="credit-content">
          <div class="credit-pie-chart">
            <div class="credit-took">80</div>
            <div class="credit-not-took">48</div>
          </div>
        </div>
        <div class="credit-description">
          <div class="took">took</div>
          <div class="remaining">remaining</div>
        </div>
      </div>
      <div></div>
      <div class="curriculum">
        <div class="title">Curriculum</div>
        <CurriculumTableVue></CurriculumTableVue>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Calendar } from 'ant-design-vue'
import CurriculumTableVue from '../components/CurriculumTable.vue'
export default {
  components: {
    ACalendar: Calendar,
    CurriculumTableVue
  }
}
</script>

<style scoped lang="scss">
:deep .ant-table-tbody > tr > td {
  font-size: 14px;
}

ul {
  list-style: none;
  margin-top: 100px;
}
.content {
  background: white;
  display: grid;
  grid-template-columns: 5% 50% 45%;
  border-top-right-radius: 20px;
  border-bottom-right-radius: 20px;
  height: 100%;
}
.second-row {
  display: grid;
  position: relative;
  padding: 20px;
  margin: 15px;
  grid-template-rows: 27% 3% 70%;
  background-color: rgb(211, 211, 211, 0.2);
  border-radius: 20px;
}
.third-row {
  display: grid;
  position: relative;
  padding: 20px;
  margin: 15px;
  grid-template-rows: 30% 3% 67%;
  background-color: rgb(211, 211, 211, 0.2);
  border-radius: 20px;
  overflow: hidden;
}
.announcement {
  background-color: rgb(0, 255, 255, 0.2);
  border-radius: 20px;
}
.announce-item {
  display: grid;
  margin-top: 5px;
  background-color: rgb(245, 245, 220, 0.3);
  grid-template-columns: 80% 20%;
  max-height: 30px;
  :nth-child(1) {
    margin-left: 10px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    color: rgb(0, 0, 0, 0.8);
  }
  :nth-child(2) {
    display: flex;
    font-size: 14px;
    margin-right: 3px;
    justify-content: flex-end;
    align-items: end;
  }
}
.credit {
  display: block;
  position: relative;
  background-color: rgb(0, 255, 255, 0.2);
  border-radius: 20px;
}
.title {
  width: 100%;
  align-items: center;
  justify-content: center;
  text-align: center;
  font-style: italic;
  color: rgb(220, 191, 147);
}
.schedule {
  background-color: rgb(0, 255, 255, 0.2);
  border-radius: 20px;
}
.curriculum {
  background-color: rgb(0, 255, 255, 0.2);
  border-radius: 20px;
  width: 100%;
  height: 100%;
  overflow-y: scroll;
}
.credit-content {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: calc(100% - 20px);
}
.credit-pie-chart {
  display: block;
  position: relative;
  width: 22%;
  padding-bottom: 22%;
  border-radius: 50%;
  background: conic-gradient(orange 0deg 225deg, gray 225deg 360deg);
}
.credit-took {
  position: absolute;
  top: 50%;
  left: 75%;
  transform: translate(-75%, -50%);
  color: white;
}
.credit-not-took {
  position: absolute;
  top: 50%;
  left: 25%;
  transform: translate(-25%, -50%);
  color: white;
}
.credit-description {
  display: flex;
  flex-direction: column;
  bottom: 3%;
  right: 3%;
  position: absolute;
  font-size: 12px;
  font-weight: bold;
}
.took {
  display: block;
  position: relative;
  font-size: 12px;
  font-weight: bold;
  color: black;
}
.took::before,
.remaining::before {
  content: '';
  display: block;
  position: absolute;
  width: 10px;
  height: 10px;
  top: 10%;
  left: -25%;
  background: orange;
}
.remaining {
  display: block;
  position: relative;
  font-size: 12px;
  font-weight: bold;
  color: black;
}
.remaining::before {
  background: gray;
}
.course {
  display: flex;
  max-height: 100%;
  max-width: 100%;
  font-size: 10px;
  text-align: center;
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
/* media */
@media (min-width: 700px) and (max-width: 1060px) {
  .course {
    overflow: hidden;
    line-height: 0.8;
  }
  .credit-pie-chart {
    width: 40%;
    padding-bottom: 40%;
  }
  .nav-item {
    margin-left: 5px;
  }
}
@media (max-width: 700px) {
  * {
    font-size: 14px;
  }
  .content {
    display: flex;
    flex-direction: column;
    border-top-right-radius: 20px;
    border-bottom-right-radius: 20px;
    height: 100%;
    padding: 20px;
    overflow: auto;
  }
  .schedule {
    margin-top: 20px;
  }
  .second-row {
    display: unset;
  }
  .third-row {
    display: unset;
    overflow: unset;
  }
  .credit-pie-chart {
    width: 15%;
    padding-bottom: 15%;
  }
}
@media (max-width: 550px) {
  .credit-pie-chart {
    width: 22%;
    padding-bottom: 22%;
  }
}
@media (max-width: 420px) {
  * {
    font-size: 12px;
  }
  .course {
    overflow: hidden;
    line-height: 0.8;
  }
  .nav-item {
    margin-left: 1px;
  }
}
</style>
