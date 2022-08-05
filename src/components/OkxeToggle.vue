<template>
    <div class="okxe-toggle">
        <input type="checkbox" v-model="checked" @change="onChange" id="checkbox" class="offscreen"  :disabled="disabled">
        <label for="checkbox" class="switch" :class="classes"></label>
        <label for="checkbox" class="okxe-toggle__text"><slot /></label>
        <!-- ahsdjk -->
    </div>
</template>
<script>

export default {
    name: 'okxe-toggle',

    props: {
        defaultChecked: {
            type: Boolean,
            default: false
        },
        disabled: {
            type: Boolean,
            default: false
        },
        label: {
            type: String,
            default: ''
        }
    },
    data() {
        return {
            checked: this.defaultChecked
        }
    },
    computed: {
        classes() {
            const result = []
            if (this.disabled) {
                result.push('disable')
            }
            return result
        }
    },
    created() {
        console.log('==================', this.classes)
    },
    methods: {
        onChange() {
            this.$emit('input', this.checked)
        }
    }
}
</script>
<style lang="sass" scoped>
.okxe-toggle
    display: flex
    justify-content: center
    align-items: center
    &__text
        margin-left: 8px
.switch
    position: relative
    display: inline-block
    width: 38px
    height: 20px
    background-color:#868D93
    border-radius: 20px
    transition: all 0.3s
.disable
    background-color: #EBECED
.switch::after
    content: ''
    position: absolute
    width: 16px
    height: 16px
    border-radius: 16px
    background: #ffffff
    top: 2px
    left: 1px
    transition: all 0.3s
input[type='checkbox']:checked + .switch::after
    transform: translateX(19px)
input[type='checkbox']:checked + .switch
    background: #00BCC3
.offscreen
    position: absolute
    left: -9999px
</style>
