<template>
    <div class="container">
        <p>域名：{{ result.ping_host }}</p>
    </div>
    <div class="button-container">
      <button @click="startLoading" >{{ loading ? 'Loading...' : '測試JS功能' }}</button>
    </div>

    <div>
        <table border="1" cellpadding="5">
            <thead>
                <tr>
                    <th>檢測點</th>
                    <th>解析 IP</th>
                    <th>解析 IP 所在地</th>
                    <th>發送 transmitted</th>
                    <th>接收 received</th>
                    <th>丟包率 packet loss</th>
                    <th>最大時間 rtt max.</th>
                    <th>最小時間 rtt min.</th>
                    <th>平均時間 rtt avg.</th>
                    <th>包大小 packet size</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="index in 5" :key="index">
                    <td>{{ result.source_ip }}</td>
                    <td>
                        <span v-if="!loading">{{ result.ping_ip }}</span>
                        <div v-else class="loading"></div>
                    </td>
                    <td>{{ result.ping_ip_geo }}</td>
                    <td>{{ result.transmitted }}</td>
                    <td>{{ result.received }}</td>
                    <td>{{ result.loss_percentage }}%</td>
                    <td>{{ result.rtt_max }} ms</td>
                    <td>{{ result.rtt_min }} ms</td>
                    <td>{{ result.rtt_avg }} ms</td>
                    <td>{{ result.packet_size }} bytes</td>
                </tr>
            </tbody>
        </table>
        <br>   
        <textarea readonly style="width: 50%; height: 300px;" class="output">{{ result.raw_output }}</textarea>
    </div>
</template>

<script setup>

import { ref } from 'vue'

const result = ref({
    ping_host: 'result.ping_host',
  source_ip: 'result.source_ip',
  ping_ip: 'result.ping_ip',
  ping_ip_geo: 'result.ping_ip_geo',
  transmitted: 'result.transmitted',
  received: 'result.received',
  loss_percentage: 'result.loss_percentage',
  rtt_max: 'result.rtt_max',
  rtt_min: 'result.rtt_min',
  rtt_avg: 'result.rtt_avg',
  packet_size: 'result.packet_size',
  raw_output: 'result.raw_output',
})


const loading = ref(false)

const startLoading = () => {
    alert("Hello! I am an alert box!!");
}

</script>


<style lang="sass" scoped>
.container
    p
        margin-bottom: 10px

table
    border-collapse: collapse
    width: 100%

    thead
        color: #fff

    th, td
        padding: 10px
    th
        background-color: #20a0ff

    tr:nth-child(even)
        background-color: #f2f2f2
    tbody
        background-color: #fff



.button-container
    margin: 20px 0
    text-align: center

    button
        background-color: #20a0ff
        color: #fff
        width: 100px
        height: 40px
        padding: 5px 10px
        border: none
        border-radius: 5px
        cursor: pointer
.loading
    width: 15px
    height: 15px
    border: 2px solid #ccc
    border-top: 2px solid #20a0ff
    border-radius: 50%
    animation: spin 1s linear infinite
    position: relative
    transform: translateX(50%)

    
@keyframes spin
    0%
        transform: rotate(0deg)
    100%
        transform: rotate(360deg)
.output
    width: 50%
    height: 300px
    background: black
    color: white
</style>
