<template>
    <div id="app">
        <router-view></router-view>
        <tab-bar>
            <tab-bar-item path="/index">
                <img slot="img" src="../public/imgs/index.png" alt="首页">
                <img slot="img-active" src="../public/imgs/index_selected.png" alt="首页">
                <p slot="title">首页</p>
            </tab-bar-item>
            <tab-bar-item path="/sale">
                <img slot="img" src="../public/imgs/sale.png" alt="热卖">
                <img slot="img-active" src="../public/imgs/sale-selected.png" alt="热卖">
                <p slot="title">热卖</p>
            </tab-bar-item>
            <tab-bar-item path="/buy">
                <img slot="img" src="../public/imgs/buy.png" alt="购物车">
                <img slot="img-active" src="../public/imgs/buy-selected.png" alt="购物车">
                <p slot="title">购物车</p>
            </tab-bar-item>
            <tab-bar-item path="/mine">
                <img slot="img" src="../public/imgs/mine.png" alt="我的">
                <img slot="img-active" src="../public/imgs/mine-selected.png" alt="我的">
                <p slot="title">我的</p>
            </tab-bar-item>
        </tab-bar>
    </div>
</template>


<script>
    import TabBar from "./components/TabBar";
    import TabBarItem from "./components/TabBarItem";

    export default {
        name: 'App',
        components: {
            TabBar,
            TabBarItem
        }
    }
</script>

<style>

</style>
