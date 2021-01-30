<template>
    <div class="lapoo">
        <div class="profile"></div>
        <div class="wrapper">
            <div class="list">
                <div class="card">
                    <div class="subject"></div>
                    <div class="describe"></div>
                </div>
                <div class="card">
                    <div class="subject"></div>
                    <div class="describe"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

@Component({
    components: {
        HelloWorld,
    },
})
export default class Home extends Vue {}
</script>

<style lang="scss" scoped>
.lapoo {
    width: 100%;
    height: 100%;
    background-color: #f3f3f3;
    display: flex;
    .profile {
        width: 400px;
        height: 100%;
        // #e1e4ff, #311080
        background-image: linear-gradient(#8276a7, #061435);
        border: none;
    }
    .wrapper {
        width: calc(100% - 400px);
        height: 100%;
        background-color: #fff;
        display: flex;
        position: relative;
        padding: 10px 0px;
        box-sizing: border-box;
        .list {
            margin: 0 auto;
            width: 800px;
            height: 100%;
            .card:first-of-type {
                margin-top: 0px;
            }
            .card {
                width: 100%;
                height: 300px;
                border: none;
                border-radius: 5px;
                background-color: #fafafa;
                margin-top: 20px;
                .subject {
                    width: 100%;
                    height: 220px;
                    background-color: #ECECEC;
                    border-radius: 5px 5px 0px 0px;
                }
                .describe {
                    width: 100%;
                    height: calc(100% - 220px);
                    background-color: #f7f7f7;
                    border-radius: 0px 0px 5px 5px;
                }
            }
        }
    }
}
</style>
