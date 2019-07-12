<template>
    <div>
        <input @input="onInput"/>
    </div>
</template>

<script>
    export default ({
        name: 'SearchBar',
        methods: {
            onInput(event) {
                const {value} = event.target;
                this.$emit('termChange', value);
            }
        }
    });
</script>

<style scoped>
    input {
        width: 75%;
    }

    div {
        text-align: center;
        margin: 20px;

    }
</style>