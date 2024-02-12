<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected: selected && !open }">
            <GiftBoxVue v-if="open && hasGiftBoxVue"/>
        </div>
        <div class="door" :class="{ open }"
            @click="selected = !selected">
            <div class="number" :class="{ selected }">{{ number }}</div>
            <div class="knob" :class="{ selected }" 
                @click.stop="open = true"></div>
        </div>
    </div>
</template>

<script>
import GiftBoxVue from './GiftBox.vue'

export default {
    components: { GiftBoxVue},
    props:{
        Number:{},
        hasGiftBoxVue: { type: Boolean }
    },
    data() {
        return{
            open: false,
            selected: false
        }
    }
}
</script>

<style>
:root{
    --dor-border: 5px solid rgba(165, 42, 42, 0.699);
    --selected-border: 5px solid yellow;
}

.door-area {
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 10px solid #AAA;
    margin-bottom: 20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;
}

.door-frame{
    position: absolute;
    height: 300px;
    width: 180px;

    border-left: var(--dor-border);
    border-top: var(--dor-border);
    border-right: var(--dor-border);

    display: flex;
    justify-content: center;
    align-items: flex-end;
}

.door{
    position: absolute;
    top: 5px;
    height: 295px;
    width: 170px;
    background: rgb(173, 80, 13);

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 15px;
}

.door .knob{
    height: 20px;
    width: 20px;
    border-radius: 10px;
    background: rgb(204, 173, 36);
    align-self: flex-start;
    margin-top: 120px;
}

.door-frame.selected{
    border-left: var(--selected-border);
    border-top: var(--selected-border);
    border-right: var(--selected-border);
}

.door > .number.selected {
    color: yellow;
}

.door > .knob.selected {
    background-color: yellow;
}

.door.open {
    background: #0007;
}

.door.open .knob{
    display: none;
}

.door.open .number {
    display: none;
}
</style>