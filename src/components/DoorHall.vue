<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected: selected && !open }">
            <GiftHall v-if="open && hasGift" />
        </div>
        <div class="door" :class="{ open }" @click="selected = !selected">
            <div class="number" :class="{ selected }">{{ number }}</div>
            <div class="knob" :class="{ selected }" @click.stop="open=true"></div>
        </div>
    </div>
</template>

<script setup lang="ts">

import { ref } from 'vue'
import GiftHall from './GiftHall.vue';

defineProps(['number', 'hasGift'])

let open = ref(false)
let selected = ref(false)

</script>

<style scoped>
:root {
    --door-border: 5px solid brown;
    --selected-border: 5px solid yellow;
}

.door-area {
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 10px solid #aaa;
    margin-bottom: 20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;
}

.door-frame {
    position: absolute;
    height: 300px;
    width: 180px;

    border-left: 5px solid brown;
    border-top: 5px solid brown;
    border-right: 5px solid brown;
    /* border-left: var(--door-border);
    border-top: var(--door-border);
    border-right: var(--door-border); */

    display: flex;
    justify-content: center;
    align-items: flex-end;
}

.door {
    position: absolute;
    top: 5px;
    height: 295px;
    width: 170px;
    background-color: chocolate;

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 10px;
}

.door .knob {
    background-color: brown;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    align-self: flex-start;
    margin-top: 60px;
}

.door-frame.selected {
    border-left: 5px solid yellow;
    border-top: 5px solid yellow;
    border-right: 5px solid yellow;
}

.door .number{
    color: black
}

.door .number.selected {
    color: yellow;
}

.door .knob.selected {
    background-color: yellow;
}

 .door.open {
    background-color: #0007;
}

 .door.open .knob {
    display: none;
}

.door.open .number {
    display: none;
}

</style>
