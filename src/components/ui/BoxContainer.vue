<template>
    <div class="row base-bg">
        <div :class="colLength">
            <slot name="GraphContent"></slot>
        </div>
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
    margin-top: 30px;
}
</style>
