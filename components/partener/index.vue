<template>
    <div class="partt">
        <el-carousel :height="$store.state.is_pc ? '100px' :'50px' " :interval="5000" arrow="always">
            <el-carousel-item
                v-for="item in list4Result"
                :key="item.title"
                class=""
            >
                <div class="width_65 phone_width_80 margin_auto display_flex flex_jusify_space">
                    <div v-for="img_obj in item"
                        class="img"
                        :key="img_obj.title">
                        <img
                            :src="img_obj.img"
                            alt
                            class="width_100"
                        />
                    </div>
                    
                </div>
            </el-carousel-item>
        </el-carousel>
        <!-- <el-carousel height="100px" :interval="5000" arrow="always">
            <el-carousel-item>
                <img src="../../static/img/b1.jpg" alt="" class="width_100">
            </el-carousel-item>
            <el-carousel-item>
                <img src="../../static/img/b2.jpg" alt="" class="width_100">
            </el-carousel-item>
            <el-carousel-item>
                <img src="../../static/img/b3.jpg" alt="" class="width_100">
            </el-carousel-item>
        </el-carousel> -->
    </div>
</template>

<script>
import isPc from "../../util/get_pc_or_phone";
import getInnerWidth from "../../util/get_width";
export default {
    props: {
        currentBanner: {
            type: Object
        }
    },
    data() {
        return {
            pc_banner: "",
            banner_height: "0px",
            list3: [{
                img: require("../../static/img/addr.png"),
                title: "Address",
                txt: "ROOM 3 27/F HO KING COMMERCIAL CENTRE NO 2-16 FA YUEN STREET MONGKOK KL",

            },
            {
                img: require("../../static/img/email.png"),
                title: "Email",
                txt: "Customer@dreamfii.com"
                }
            ],
            
            list4: [{
                img: require("../../static/img/parteners/ais.png"),
                title: "Facebook",
            },
            {
                img: require("../../static/img/parteners/celcom.png"),
                title: "Google",
                },
            
            {
                img: require("../../static/img/parteners/digi.png"),
                title: "Truemove",
            },
            {
                img: require("../../static/img/parteners/dtac.png"),
                title: "Digi",
            },
            {
                img: require("../../static/img/parteners/facebook.png"),
                title: "Dtac",
            },
            {
                img: require("../../static/img/parteners/google.png"),
                title: "Celcom",
            },
            {
                img: require("../../static/img/parteners/maxis.png"),
                title: "Vodafone",
            },
            {
                img: require("../../static/img/parteners/o2.png"),
                title: "Orange",
            },
            {
                img: require("../../static/img/parteners/orange.png"),
                title: "O2",
            },
            {
                img: require("../../static/img/parteners/t.png"),
                title: "O2",
            },
            {
                img: require("../../static/img/parteners/vodafone.png"),
                title: "O2",
            },
            {
                img: require("../../static/img/parteners/wind.png"),
                title: "O2",
            }

            ]
        };
    },
    computed: {
        currentBanner_: {
            get() {
                return this.currentBanner;
            }
        },
        list4Result(){
            var result = [];
            var data = this.list4;
            for(var i=0;i<data.length;i+=4){
                result.push(data.slice(i,i+4));
            }
            return result
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
            });
        },
        setHeight() {
            this.$nextTick(() => {
                this.banner_height =
                    (parseInt(
                        this.$jquery(this.$jquery(".el-carousel__mask")[0]).css(
                            "width"
                        )
                    ) / 3 || getInnerWidth() / 3) + "px";
            });
        },
        watchWidth() {
            window.addEventListener("resize", () => {
                this.setHeight();
            });
        }
    }
};
</script>

<style lang='less'>
.partt {
    .el-carousel__item{
        background: #ffffff;
    }
    .img{
        width:200px;
    }
}
// phone style
@media screen and (max-width: 800px){
    .partt {
        .img{
            width:30%;
        }
    }
}
</style>