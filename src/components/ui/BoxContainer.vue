<template>
    <div :class="'white-bg rounded-2 ' + colLength">
        <slot name="GraphContent"></slot>
    </div>
</template>

<script>
export default {
    props: {
        columnLength: {
            type: String,
            default: '3'
        }
    },

    setup(props) {
        const colLength = `col-${props.columnLength}`;

        return { colLength };
    },
    name: 'BoxContainer'
};
</script>

<style scoped>
div {
    margin: 30px;
}
</style>
