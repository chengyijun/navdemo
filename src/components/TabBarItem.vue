<template>

    <div class="tabbar-item" @click="clickHandle">
        <div v-show="!isActive">
            <slot name="img"></slot>
        </div>
        <div v-show="isActive">
            <slot name="img-active"></slot>
        </div>
        <div :class="{active: isActive, title: true}">
            <slot name="title"></slot>
        </div>
    </div>
</template>

<script>

    export default {
        name: "TabBarItem",
        data() {
            return {
                // isActive: false
            }
        },
        computed: {
            isActive: {
                get() {
                    if (this.$route.matched.length > 0)
                        return this.$route.matched[0].path === this.path
                    return false
                },
                set() {

                }
            }
        },
        props: {
            path: {
                type: String,
                default() {
                    return ''
                }
            }
        },
        methods: {
            clickHandle() {
                // 路由跳转
                if (this.$route.matched[0].path !== this.path)
                    this.$router.replace(this.path)
            }
        },
        beforeRouteLeave(to, from, next) {
            console.log(11111);
            next()
        }
    }
</script>

<style>
    .tabbar-item {
        flex: 1;
        text-align: center;
    }


    .tabbar-item img {
        width: 29px;
        height: 29px;
    }

    .title {
        font-size: 16px;
        position: relative;
        top: -5px;
    }

    .title.active {
        font-size: 16px;
        position: relative;
        top: -5px;
        color: #1AFA29;
    }
</style>