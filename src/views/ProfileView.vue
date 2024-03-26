<template>
  <div class="content">
    <Collapse
      :key="1"
      header="User Info"
      style="width: 100%; overflow: auto"
      :default-active-key="['1', '2', '3']"
    >
      <CollapsePanel header="user info" :key="1">
        <Descriptions :bordered="true" :column="1">
          <DescriptionsItem label="name">
            <input type="text" v-model="userInfo.name" />
          </DescriptionsItem>
          <DescriptionsItem label="age">
            <input type="text" v-model="userInfo.age" />
          </DescriptionsItem>
          <DescriptionsItem label="birth">
            <input type="text" v-model="userInfo.birth" />
          </DescriptionsItem>
        </Descriptions>
      </CollapsePanel>
      <CollapsePanel header="account info" :key="2">
        <Descriptions :bordered="true" :column="1">
          <DescriptionsItem label="account">
            <input type="text" v-model="userInfo.account" />
          </DescriptionsItem>
          <DescriptionsItem label="identity">
            <input type="text" v-model="userInfo.identity" />
          </DescriptionsItem>
        </Descriptions>
      </CollapsePanel>
      <CollapsePanel header="contact information" :key="3">
        <Descriptions :bordered="true" :column="1">
          <DescriptionsItem label="mail">
            <input type="text" v-model="userInfo.mail" />
          </DescriptionsItem>
          <DescriptionsItem label="phone-number">
            <input type="text" v-model="userInfo.phoneNumber" />
          </DescriptionsItem>
          <DescriptionsItem label="address">
            <input type="text" v-model="userInfo.address" />
          </DescriptionsItem>
        </Descriptions>
      </CollapsePanel>
    </Collapse>
  </div>
</template>

<script setup>
import { Collapse, CollapsePanel, Descriptions, DescriptionsItem } from 'ant-design-vue'
import { ref } from 'vue'
const userInfo = ref({
  name: 'Bob',
  age: '20',
  birth: '2004-1-1',
  account: 'root',
  identity: 'student',
  mail: 'root@gmail.com',
  phoneNumber: '0912345678',
  address: '-'
})
</script>

<style scoped>
.content {
  display: flex;
  background-color: rgb(255, 255, 255);
  padding: 10px;
}
input[type='text'] {
  border: none;
  outline: none;
}
</style>
