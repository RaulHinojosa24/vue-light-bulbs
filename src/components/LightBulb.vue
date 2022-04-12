<script>
    export default {
        props: ["neededClicks"],
        emits: ["switchedOn"],
        data() {
            return {
                isOn: false,
                clicks: +this.neededClicks
            }
        },
        methods: {
            onClick() {
                this.clicks--;
                
                if (this.clicks == 0) {
                    this.isOn = !this.isOn;
                    this.$emit("switchedOn");
                }
            }
        }
    }
</script>

<template>
    <div class="bulb" :class="isOn ? 'on' : 'off'" @click="(!isOn) ? onClick() : ''">
        <h2 v-if="!isOn">{{ clicks }}</h2>
    </div>
</template>
    
<style scoped>
    .bulb {
        width: 265px;
        height: 400px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 1.5rem;
        cursor: pointer;
        user-select: none;
    }

    .bulb.on {
        background-image: url('lighton.png');
    }

    .bulb.off {
        background-image: url('lightoff.png');
    }
</style>