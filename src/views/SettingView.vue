<template>
  <div class="content">
    <Descriptions
      :column="1"
      :bordered="true"
      style="width: 100%; overflow: auto"
      class="custom-descriptions"
      :label-style="labelStyle"
    >
      <DescriptionsItem label="phone number">
        <Dropdown>
          <DropdownButton @click.prevent>{{ privacy[phoneIndex] }} </DropdownButton>
          <template v-slot:overlay>
            <Menu>
              <MenuItem v-for="(item, index) in privacy" :key="index" @click="phoneIndex = index"
                ><a>{{ item }}</a></MenuItem
              >
            </Menu>
          </template>
        </Dropdown>
      </DescriptionsItem>
      <DescriptionsItem label="address">
        <Dropdown>
          <DropdownButton @click.prevent>{{ privacy[addressIndex] }} </DropdownButton>
          <template v-slot:overlay>
            <Menu>
              <MenuItem v-for="(item, index) in privacy" :key="index" @click="phoneIndex = index"
                ><a>{{ item }}</a></MenuItem
              >
            </Menu>
          </template>
        </Dropdown></DescriptionsItem
      >
      <DescriptionsItem label="notifications"
        ><Switch v-model:checked="switchValue"></Switch
      ></DescriptionsItem>
    </Descriptions>
  </div>
</template>
<script setup>
import {
  Descriptions,
  DescriptionsItem,
  Dropdown,
  Menu,
  MenuItem,
  DropdownButton,
  Switch
} from 'ant-design-vue'
import { ref } from 'vue'
const privacy = ['Nobody', 'Everybody', 'My contacts']
const phoneIndex = ref(0)
const addressIndex = ref(0)
const switchValue = ref(true)
const labelStyle = { width: '300px' }
</script>
<style scoped>
.content {
  display: flex;
  width: 100%;
  height: 100%;
  padding: 10px;
  background-color: rgb(255, 255, 255);
}
</style>
