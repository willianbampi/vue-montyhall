<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected: selected && !open }">
            <Gift v-if="open && hasGift"></Gift>
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

    import Gift from './Gift'

    export default {
        name: 'Door',
        components: { Gift },
        props: {
            number: {},
            hasGift: { type: Boolean }
        },
        data: function() {
            return {
                open: false,
                selected: false
            }
        }
    }

</script>

<style>
    :root {
        --dor-border: 5px solid #5c4d3c;
        --selected-border: 5px solid #f9c74f;
    }

    .door-area {
        position: relative;
        width: 200px;
        height: 310px;
        border-bottom: 10px solid #edf2fb;
        margin-bottom: 20px;
        font-size: 3rem;
        display: flex;
        justify-content: center;
    }

    .door-frame {
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

    .door {
        position: absolute;
        top: 5px;
        height: 295px;
        width: 170px;
        background-color: #997b66;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 20px;
    }

    .door .knob {
        height: 20px;
        width: 20px;
        border-radius: 10px;
        background-color: #5c4d3c;
        align-self: flex-start;
        margin-top: 60px;
    }

    .door-frame.selected {
        border-left: var(--selected-border);
        border-top: var(--selected-border);
        border-right: var(--selected-border);
    }

    .door .number.selected {
        color: #f9c74f;
    }

    .door .knob.selected {
        background-color: #f9c74f;
    }

    .door.open {
        background-color: #0008;
    }

    .door.open .knob {
        display: none;
    }

    .door.open .number {
        display: none;
    }
</style>
