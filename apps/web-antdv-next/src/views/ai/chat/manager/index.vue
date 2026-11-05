<script lang="ts" setup>
import { ref } from 'vue';

import {  Page } from '@vben/common-ui';

import { TabPane, Tabs } from 'antdv-next';

import ChatConversationList from './modules/conversation-list.vue';
import ChatMessageList from './modules/message-list.vue';

const activeTabName = ref('conversation');
</script>

<template>
  <Page auto-content-height>
    <Tabs v-model:active-key="activeTabName">
      <TabPane tab="对话列表" key="conversation">
        <ChatConversationList />
      </TabPane>
      <TabPane tab="消息列表" key="message">
        <ChatMessageList />
      </TabPane>
    </Tabs>
  </Page>
</template>
