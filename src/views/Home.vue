<template>
    <div class="lapoo">
        <div class="nav">
            <div v-for="item of nav" :key="item.$key" :class="item.class" @click="onNavigate(item)">
                {{ item.label }}
            </div>
        </div>
        <div class="wrapper">
            <div class="search"></div>
            <div class="content">
                <div class="item">
                    <div class="image">
                        <div class="describe">如何提升.NET的性能</div>
                    </div>
                    <div class="tags">
                        <div class="tag">.NET</div>
                    </div>
                </div>
            </div>
        </div>
        <router-view />
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { Navigates } from '@/data/index';

@Component({
    data: () => {
        return {
            nav: Navigates,
        };
    },
    components: {},
    methods: {
        onNavigate(item) {
            const actived = (this.$data.nav as any[]).find((m) => m.class.indexOf('active') > -1);
            actived.class.splice(actived.class.indexOf('active'), 1);
            item.class.push('active');
        },
        require(path) {
            return require(path);
        },
    },
})
export default class Home extends Vue {}
</script>

<style lang="scss" scoped>
* {
    transition: all 0.5s;
}
.lapoo {
    display: flex;
    justify-content: center;
    width: 100%;
    height: 100%;
    margin: 0 auto;
    background-image: linear-gradient(to bottom right, #536aaf, #54a1e8);
    padding: 10px;
    box-sizing: border-box;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans',
        'Helvetica Neue', sans-serif;
    font-size: 14px;
    .nav {
        width: 200px;
        height: 400px;
        background-color: #fafafa2e;
        border-radius: 3px;
        padding: 5px;
        box-sizing: border-box;
        position: relative;
        .item {
            width: 100%;
            height: 40px;
            margin-top: 5px;
            line-height: 40px;
            padding-left: 5px;
            box-sizing: border-box;
            border-radius: 3px;
            font-weight: 600;
            color: #1e2e5d;
            cursor: pointer;
            outline: none;
            background-color: #fafafab0;
        }
        .item:first-of-type {
            margin-top: 0px;
        }
        .item:hover {
            background-color: #fafafab5;
            margin-left: -25px;
            width: 215px;
            transition-delay: 0.1s;
        }
        .item.active {
            background-color: #fafafab5;
            width: 188px;
            margin-left: -40px;
            width: 220px;
        }
        .item.active.net {
            background-color: #4e2fd4;
            color: #fff;
        }
        .item.active.angular {
            background-color: #c14545;
            color: #fff;
        }
    }
    .wrapper {
        width: 600px;
        height: 100%;
        margin-left: 5px;
        .search {
            width: 100%;
            height: 45px;
            margin-bottom: 5px;
            background-color: #fafafa2e;
            border-radius: 3px;
        }
        .content {
            width: 100%;
            height: calc(100% - 50px);
            background-color: #fafafa2e;
            border-radius: 3px;
            padding: 5px 5px 0px 5px;
            box-sizing: border-box;
            overflow-y: auto;
            .item {
                width: 100%;
                height: 180px;
                border-radius: 3px;
                margin-bottom: 20px;
                .image {
                    width: 100%;
                    height: calc(100% - 35px);
                    background-color: rgb(219, 215, 215);
                    position: relative;
                    background-image: url('../static/images/demo.png');
                    .describe {
                        position: absolute;
                        bottom: 0px;
                        left: 0px;
                        right: 0px;
                        height: 40px;
                        background-color: #4a4a4a80;
                        color: #fff;
                        font-weight: 600;
                        font-size: 15px;
                        line-height: 40px;
                        padding: 0px 7px;
                        letter-spacing: 1.5px;
                    }
                }
                .tags {
                    height: 35px;
                    line-height: 35px;
                    display: flex;
                    align-items: center;
                    background: #fafafa47;
                    padding: 0px 5px;
                    .tag {
                        width: fit-content;
                        box-sizing: border-box;
                        line-height: 0px;
                        padding: 0px 10px;
                        background-color: #4e2fd4;
                        color: #fff;
                        font-size: 12px;
                        height: 25px;
                        line-height: 25px;
                        border-radius: 5px;
                    }
                }
            }
            .item:last-of-type {
                margin-bottom: 5px;
            }
        }
        .content::-webkit-scrollbar {
            width: 0px;
        }
    }
}
</style>
