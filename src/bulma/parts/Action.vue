<template>
    <div class="level-item">
        <component :is="tag"
            :class="['button', { 'is-loading': loading }, button.class]"
            :disabled="disabled"
            @click="$emit('click')">
            <span class="is-hidden-mobile">
                {{ i18n(button.label) }}
            </span>
            <span class="icon">
                <fa :icon="button.icon"/>
            </span>
            <span class="is-hidden"/>
        </component>
    </div>
</template>

<script>
export default {
    name: 'Action',

    inject: ['i18n'],

    props: {
        button: {
            type: Object,
            required: true,
        },
        disabled: {
            type: Boolean,
            default: false,
        },
        loading: {
            type: Boolean,
            default: false,
        },
        tag: {
            type: String,
            required: true,
            validator: v => ['a', 'button'].includes(v),
        },
    },
};
</script>