<template>
    <div id="tab-bar">
        <slot></slot>
    </div>
</template>

<script>


    export default {
        name: "TabBar",
    }
</script>

<style>

    * {
        margin: 0;
        padding: 0;
    }

    #tab-bar {
        display: flex;
        /*background-color: red;*/
        height: 49px;
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
    }


</style>