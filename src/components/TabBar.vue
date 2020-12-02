<template>
    <div id="nav-bar">
        <a slot="item" class="navbar-item" v-for="(img,index) in imgs" @click="clickHandle(index)">
            <img v-show="!img.is_selected" :src="img.url" alt="">
            <img v-show="img.is_selected" :src="img.url_selected" alt="">
            <p v-if="img.is_selected" class="active">{{img.title}}</p>
            <p v-else>{{img.title}}</p>
        </a>
    </div>
</template>

<script>
    import TabBarItem from "./TabBarItem";

    const items = document.getElementsByClassName('navbar-item')
    const ps = document.getElementsByTagName('p')
    export default {
        name: "TabBar",
        components: {
            TabBarItem
        },
        data() {
            return {
                imgs: [
                    {
                        url: require('../../public/imgs/index.png'),
                        url_selected: require('../../public/imgs/index_selected.png'),
                        title: '首页',
                        is_selected: true
                    },
                    {
                        url: require('../../public/imgs/sale.png'),
                        url_selected: require('../../public/imgs/sale-selected.png'),
                        title: '热销',
                        is_selected: false
                    },
                    {
                        url: require('../../public/imgs/buy.png'),
                        url_selected: require('../../public/imgs/buy-selected.png'),
                        title: '购物车',
                        is_selected: false
                    },
                    {
                        url: require('../../public/imgs/mine.png'),
                        url_selected: require('../../public/imgs/mine-selected.png'),
                        title: '我的',
                        is_selected: false
                    },
                ],
                paths: [
                    '/index',
                    '/sale',
                    '/buy',
                    '/mine'
                ]
            }
        },
        methods: {
            clickHandle(index) {

                // 设置导航栏图标的选中状态
                for (const img of this.imgs) {
                    img.is_selected = false
                }
                this.imgs[index].is_selected = true
                // 设置导航栏标题的选中状态
                for (const p of ps) {
                    if (p.classList.contains('active')) {
                        p.classList.remove('active')
                    }
                }
                items[index].lastChild.classList.add('active')

                // 路由跳转
                if (this.$route.matched[0].path !== this.paths[index])
                    this.$router.replace(this.paths[index])
            }
        }
    }
</script>

<style>

    * {
        margin: 0;
        padding: 0;
    }

    #nav-bar {
        display: flex;
        /*background-color: red;*/
        height: 49px;
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
    }

    .navbar-item {
        flex: 1;
        text-align: center;
    }


    .navbar-item img {
        width: 29px;
        height: 29px;
    }

    .navbar-item p {
        font-size: 16px;
        position: relative;
        top: -5px;
    }

    .navbar-item p.active {
        font-size: 16px;
        position: relative;
        top: -5px;
        color: #1AFA29;
    }

</style>