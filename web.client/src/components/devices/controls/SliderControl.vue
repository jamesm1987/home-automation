<template>
    <form class="slider">
        <input
            type="range"
            :min="min"
            :max="max"
            v-model="currentValue"

            @change="$emit('input', $event.target.value)"

            :name="name"
        />

        <output>
            {{ currentValue }}
        </output>
    </form>
</template>

<script>
    export default {
        name: 'SliderControl',

        props: {
            value: {
                type: Number,
                required: true,
            },

            name: {
                type: String,
                required: false,
                default: 'slider',
            },

            min: {
                type: Number,
                required: false,
                default: 0,
            },

            max: {
                type: Number,
                required: false,
                default: 100,
            }
        },

        data() {
            return {
                currentValue: this.value,
            }
        },

        watch: {
            value: function (newValue) {
                this.currentValue = newValue;
            },
        },
    }
</script>
