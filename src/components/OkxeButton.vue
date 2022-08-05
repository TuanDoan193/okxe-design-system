<template>
    <div class="button-component"  :class="classes">
        <v-btn
            depressed
            @click="onClick"
            :style="styles"
            :disabled="disabled"
            :color="backgroundColor"
        >
            <v-layout d-flex align-center justify-center>
                <div class="button-component__icon" v-if="$slots['icon']">
                    <slot name="icon"/>
                </div>
                <div v-if="label" class="button-component__label" >
                    {{ label }}
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
        label: {
            type: String,
            default: ''
        },
        icon: {
            type: String,
            default: ''
        },
        large: {
            type: Boolean,
            default: false
        },
        medium: {
            type: Boolean,
            default: false
        },
        small: {
            type: Boolean,
            default: false
        },
        width: {
            type: String,
            default: ''
        },
        backgroundColor: {
            type: String,
            default: '#00BCC3'
        },
        disabled: {
            type: Boolean,
            default: false
        },
        colorText: {
            type: String,
            default: ''
        },
        outLinedColor: {
            type: String,
            default: ''
        },
        borderRadius: {
            type: String,
            default: ''
        },
        circleButtonMedium: {
            type: Boolean,
            default: false
        },
        circleButtonSmall: {
            type: Boolean,
            default: false
        },
        circleButtonLarge: {
            type: Boolean,
            default: false
        },
        circleButton: {
            type: String,
            default: ''
        },
        bottomFixed: {
            type: Boolean,
            default: false
        },
    },
    computed: {
        styles() {
            const styles = {};
            if (this.colorText) {
                styles["color"] = this.colorText;
            }
            if (this.width) {
                styles["width"] = this.width.includes('px') ? this.width + ' !important' : this.width + 'px !important'
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
            switch (this.circleButton) {
                case 'large':
                case 'medium':
                case 'small':
                    result.push('circle-button');
                    result.push('circle-button__' + this.circleButton)
                    break;
                default:
                    break
            }
            return result;
        }
    },
    created() {
        // console.log('thadiohsiodhas', this.styles)
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
    margin: 12px 16px 24px
    .v-btn
        width: 200px
        height: 48px !important
        color: #ffffff
        background-color: #00BCC3
        min-width: 0
        border-radius: 8px
        .layout
            flex: 0 0 auto
            .button-component__icon
                margin-right: 8px
    .v-btn::before
        background-color: transparent
    .v-btn:not(.v-btn--round).v-size--default
        min-width: 0 !important
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
    &.circle-button > .v-btn
        border-radius: 50%
        .button-component__icon
            padding-right: 0 !important
            margin-right: 0 !important
    &.circle-button__large > .v-btn
        width: 48px !important
        height: 48px !important
    &.circle-button__medium > .v-btn
        width: 36px !important
        height: 36px !important
    &.circle-button__small > .v-btn
        width: 32px !important
        height: 32px !important
    &.circle-button-large > .v-btn
        border-radius: 50%
        width: 48px !important
        height: 48px !important
        .button-component__icon
            padding-right: 0 !important
            margin-right: 0 !important
    &.circle-button-medium > .v-btn
        border-radius: 50%
        width: 36px !important
        height: 36px !important
        .button-component__icon
            padding-right: 0 !important
            margin-right: 0 !important
    &.circle-button-small > .v-btn
        border-radius: 50%
        width: 32px !important
        height: 32px !important
        .button-component__icon
            margin-right: 0 !important
            padding-right: 0 !important
    &.bottom-fixed > .v-btn
        bottom: 0
        flex: 1 1 auto
        left: 50%
        position: fixed
        transform: translateX(-50%)
        z-index: 2
        margin: 0
        width: 720px !important
        max-width: 100% !important
    &.disabled > .v-btn
        background-color: #D6D9DB
        cursor: not-allowed
.button-component__label
    font-size: 14px
    font-style: normal
    font-weight: 600
    text-transform: none
    &::first-letter
        text-transform: capitalize !important
</style>