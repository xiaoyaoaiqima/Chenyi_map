<template>
    <div>
        <div class="container">
            <el-input v-model="inputTime" placeholder="输入时间"></el-input>
            <el-button @click="showEvent" :icon="Search">显示事件</el-button>
        </div>
        <el-card v-if="event" style="max-width: 800px">
            <template #header>
                <div class="card-header">
                    <span>{{ event.event }}</span>
                </div>
            </template>
            <el-text class="mx-1" type="primary">{{ event.date }}</el-text>
            <el-text class="mx-1">{{ event.phrase }}</el-text>
        </el-card>
        <div id="map"></div>
    </div>
</template>

<script setup>
import {
    Search,
} from '@element-plus/icons-vue'
import { ref, onMounted } from 'vue';
import L from 'leaflet';
import 'leaflet/dist/leaflet.css';
import eventData from '../assets/data.json';

const inputTime = ref('');
const map = ref(null);
const event = ref(eventData[0]);

onMounted(() => {
    map.value = L.map('map').setView([30, 104], 10);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map.value);
});

const showEvent = () => {
    const events = eventData;
    const inputDate = new Date(inputTime.value);
    let foundEvent = null;

    if (isNaN(inputDate)) {
        return;
    }

    if (inputTime.value.includes('-')) {
        foundEvent = events.find(item => item.date === inputTime.value);
        console.log(foundEvent.lat);
    } else {
        foundEvent = events.find(item => {
            const eventDate = new Date(item.date);
            return eventDate.getFullYear() === inputDate.getFullYear();
        });
    }

    if (foundEvent) {
        event.value = foundEvent;
        if (foundEvent.lat !== null && foundEvent.lng !== null) {
            const marker = L.marker([foundEvent.lat, foundEvent.lng]).addTo(map.value);
            map.value.setView([foundEvent.lng, foundEvent.lat], 13);
        } else {
            alert("Error: Invalid latitude or longitude");
        }
    } else {
        event.value = null;
    }
};
</script>

<style>
.container {
    display: flex;
    align-items: center;
}

#map {
    height: 600px;
    width: 800px;
}
</style>