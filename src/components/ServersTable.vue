<template>
  <table class="ui basic unstackable table" id="table">
    <thead>
    <tr>
      <th id="status4">运行状态</th>
      <th id="alias">节点名</th>
      <th id="type">类型</th>
      <th id="location">服务器位置</th>
      <th id="uptime">在线时间</th>
      <th id="load_5">负载</th>
      <th id="network">网络(B/s) ↓|↑</th>
      <th id="traffic">流量(B) ↓|↑</th>
      <th id="cpu">CPU</th>
      <th id="ram">内存</th>
      <th id="hdd">硬盘</th>
    </tr>
    </thead>
    <tbody id="servers">
    <!-- Servers here \o/ -->
    <!--
    use index for the key may cause performance issues when delete a server from array,
    but not a big matter and we cannot find a more suitable data for the unique key.
    -->
    <table-item v-for="(server, index) of servers" :key="index" :server="server"/>
    </tbody>
  </table>
</template>
<script lang="ts">
import { defineComponent, PropType } from 'vue';
import TableItem from '@/components/TableItem.vue';
import { StatusItem } from '@/types';

export default defineComponent({
  name: 'ServersTable',
  props: {
    servers: {
      type: Array as PropType<Array<StatusItem>>,
      default: () => ([])
    }
  },
  components: {
    TableItem
  }
});
</script>
<style>
#table {
  font-size: 1rem;
  border: none;
  text-align: center;
  vertical-align: middle;
}

#table thead tr th {
  color: #9da2a6;
  white-space: nowrap;
}
</style>
