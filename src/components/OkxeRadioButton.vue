<template>
    <v-radio-group v-if="options && options.length > 0" v-model="radioModel">
        <v-radio v-for="(o, i) in options" :key="i" :label="o.text" :value="o.value"  :disabled="isDisabled" color='red'  />
    </v-radio-group>
</template>
<script>
export default {
    props: {
        label: {
            type: String,
            default: ''
        },
        isDisabled: {
            type: Boolean,
            default: false
        },
        value: {
            type: [String, Number, Boolean],
            default: ''
        },
        color: {
            type: String,
            default: '#00BCC3'
        },
        options: {
            type: Array,
            default: null
        }
    },
    data() {
        return {
            radioModel: this.value
        }
    }
}
</script>