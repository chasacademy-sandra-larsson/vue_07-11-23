<template>
    <button :class="btnClass" @click="handleClick">
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: 'CustomButton',
    props: {
        btnClass: {
            type: String,
            required: false,
            default: 'default-btn'
        }
    },
    methods: {
        handleClick() {
            this.$emit('custom-btn-clicked')
        }
    }
}
</script>

<style scoped>

button {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 15px;
    border-radius: 4px;
    border: 1px solid #ccc;
    cursor: pointer;
}

.default-btn {
    background-color: #f8f8f8;
}

.primary {
    background-color: #007bff;
    color: #fff;
}

.secondary {
    background-color: #6c757d;
}
</style>