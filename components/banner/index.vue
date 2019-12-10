<template>
    <div class="position_relative">
        <h1 class="pcs font_size_50 white">
            Buying solution for hero APP
        </h1>
        <el-carousel class="xxx" :height="$store.state.is_pc ? banner_height : '400px'" :interval="5000" :arrow="$store.state.is_pc ? 'always':''">
            <el-carousel-item>
                <img src="../../static/img/b1.png" :height="$store.state.is_pc ? banner_height : '400px'"  style="" alt="" class="width_100">
            </el-carousel-item>
            <el-carousel-item>
                <img src="../../static/img/b2.png" :height="$store.state.is_pc ? banner_height : '400px'"  alt="" class="width_100">
            </el-carousel-item>
            <!-- <el-carousel-item>
                <img src="../../static/img/b3.jpg" :height="$store.state.is_pc ? banner_height : '300px'"  alt="" class="width_100">
            </el-carousel-item> -->
        </el-carousel>
    </div>
</template>

<script>
    import isPc from "../../util/get_pc_or_phone"
    import getInnerWidth from "../../util/get_width"
    export default {
        props: {
            currentBanner: {
                type: Object
            }
        },
        data() {
            return {
                pc_banner: '',
                banner_height: "0px"
            }
        },
        computed: {
            currentBanner_: {
                get() {
                    return this.currentBanner
                },
            }
        },
        mounted() {
            this.setHeight();
            this.watchWidth();
        },
        methods: {
            jumpBanner(mp4id) {
                this.$router.push({
                    path: "/" + mp4id
                })
            },
            setHeight() {
                this.$nextTick(() => {
                    this.banner_height = (parseInt(this.$jquery(this.$jquery('.el-carousel__mask')[0]).css("width")) / 2 || getInnerWidth() / 2) + "px";
                })
            },
            watchWidth() {
                window.addEventListener("resize", () => {
                    this.setHeight();
                })
            },
            
        }
    }
</script>

<style lang='less'>
    .el-carousel__item:nth-child(2n) {
        background-color: #99a9bf;
    }
    
    .el-carousel__item:nth-child(2n+1) {
        background-color: #d3dce6;
    }
</style>