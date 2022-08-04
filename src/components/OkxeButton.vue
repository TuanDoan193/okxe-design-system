<template>
    <div class="button-component"  :class="classes">
        <v-btn flat @click="onClick" :style="styles" :disabled="disabled">
            <v-layout align-center justify-center>
                <div class="button-component__icon pr-2" v-if="$slots['icon']">
                    <slot name="icon"/>
                </div>
                <div v-if="label" class="button-component__label" >
                    <slot name="label"/>
                </div>
                <slot />
            </v-layout>
        </v-btn>
    </div>
</template>
<script>
export default {
    name: 'button-component',
    props: {
        label: String,
        icon: String,
        large: Boolean,
        medium: Boolean,
        small: Boolean,
        width: String,
        backgroundColor: String,
        disabled: Boolean,
        colorText: String,
        outLinedColor: String,
        borderRadius: String,
        circleButtonMedium: Boolean,
        circleButtonSmall: Boolean,
        bottomFixed: Boolean,
    },
    computed: {
        styles() {
            const styles = {};
            if (this.colorText) {
                styles["color"] = this.colorText;
            }
            if (this.width) {
                styles["width"] = this.width.includes('px') ? this.width : this.width + 'px'
            }
            if (this.borderRadius) {
                styles["border-radius"] = this.borderRadius.includes('px') ? this.borderRadius : this.borderRadius   + 'px'
            }
            if (this.backgroundColor) {
                styles["background-color"] = this.backgroundColor
            }
            return styles;
        },
        classes() {
            const result = []
            if (this.large) {
                result.push("large")
            }
            if (this.medium) {
                result.push("medium")
            }
            if (this.small) {
                result.push("small")
            }
            if (this.backgroundColor) {
                result.push('background-' + this.backgroundColor)
            }
            if (this.circleButtonMedium) {
                result.push('circle-button-medium')
            }
             if (this.circleButtonSmall) {
                result.push('circle-button-small')
            }
            if (this.bottomFixed) {
                result.push('bottom-fixed')
            }
            if (this.disabled) {
                result.push('disabled')
            }
            return result;
        }
    },
    created() {
    },
    methods: {
        onClick(e) {
            this.$emit("click", e);
        }
    }
}
</script>
<style lang="sass" scoped>
.button-component
    background-color: transparent
    .v-btn
        width: 200px
        height: 48px
        color: #ffffff
        background-color: #00BCC3
        min-width: 0
        border-radius: 8px
    .v-btn::before
        background-color: transparent
    &.background-white > .v-btn
        background-color: #fff
        .button-component__label
            color: #00bcc3
        border: 1px solid #00BCC3
    &.background-gray > .v-btn
        background-color: #D6D9DB
        color: #ffffff
    &.background-default > .v-btn
        background-color: #00BCC3
        color: #ffffff
        &:hover
            background-color: #00A9B0
    &.large > .v-btn
        height: 48px !important
    &.medium > .v-btn
        height: 40px !important
    &.small > .v-btn
        height: 32px !important
    &.circle-button-medium > .v-btn
        border-radius: 50%
        width: 48px
        height: 48px
        .button-component__icon
            padding-right: 0 !important
    &.circle-button-small > .v-btn
        border-radius: 50%
        width: 36px
        height: 36px
        .button-component__icon
            padding-right: 0 !important
    &.bottom-fixed > .v-btn
        bottom: 0
        flex: 1 1 auto
        left: 50%
        position: fixed
        transform: translateX(-50%)
        z-index: 2
        margin: 0
    &.disabled > .v-btn
        background-color: #D6D9DB
        cursor: not-allowed
    &.out-line > .v-btn
.button-component__label
    font-size: 14px
    font-style: normal
    font-weight: 600
    &::first-letter
        text-transform: capitalize
</style>