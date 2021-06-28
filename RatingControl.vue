<template>
    <ul>
        <li :class="{active: activeOption === 'POOR'}"><button type="button" @click="activate">POOR</button></li>
        <li :class="{active: activeOption === 'AVERAGE'}"><button type="button" @click="activate">AVERAGE</button></li>
        <li  :class="{active: activeOption === 'EXCELLENT'}"><button type="button" @click="activate">EXCELLENT</button></li>
        
    </ul>
</template>

<script>
export default {
    props: ['modelValue'],
    emits: ['update:modelValue'],
    data() {
        return {
            activeOption: this.modelValue,
            };
    },
    methods: {
        activate(option) {
            this.activeOption = option;
            this.$emit('update:modelValue', option);
        },
    }
}
</script>

<style scoped>
.active {
    border-color: red;
}
.active button {
    color: red;
}
ul{
    list-style: none;
    margin: 0.5rem 0;
    padding: 0;
    display: flex;
}
li{
    margin: 0 1rem;
    border: 1px solid red;
    padding: 1rem;
    display: flex;
    justify-content: center;
    align-items: center;
}
button{
    font: inherit;
    border: none;
    background-color: transparent;
    cursor: pointer;
}
</style>