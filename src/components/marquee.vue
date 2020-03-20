<template>
    <section ref="myMarquee" class="join">
        <div class="join-content" ref="marqueeWrapper">
            <!-- ul和li的节点层级一定不能改变，ul下面的子节点必须是li，不然取不到offsetLeft的值 -->
            <ul class="join-content-wrap" ref="ul">
                <li class="join-content-item" v-for="(item, index) in [...joinList, ...joinList]" :key="index">
                    <div class="join-content-item-img">
                        <img :src="item.avatar" alt="">
                    </div>
                    <div class="join-content-item-txt">
                        <span class="name">恭喜 {{item.nickname}}</span>
                    </div>
                </li>
            </ul>
        </div>
    </section>
</template>

<script>
    // @ is an alias to /src
    export default {
        data() {
            return {
                wrapperElement: null,
                ulElement: null,
                timerId: null,
            }
        },
        methods: {
            move(speed) {
                let that = this;
                this.wrapperElement = this.$refs.marqueeWrapper;
                this.ulElement = this.$refs.ul;
                let liElementArr = this.$refs.ul.childNodes;
                let resultNum;
                for (let i = 0; i < liElementArr.length; i++) {
                    resultNum += liElementArr.item(i).offsetWidth; //只能这样写才能拿到offsetwidth
                }
                this.ulElement.style.width = resultNum + 'px';
                //向左滚动（speed为-）
                if (that.ulElement.offsetLeft < (-that.ulElement.offsetWidth / 2)) {
                    that.ulElement.style.left = '0'; //that.ulElement的左边框与div的左边框对齐
                }
                //向右滚动（speed为+）
                if (that.ulElement.offsetLeft > 0) {
                    that.ulElement.style.left = -(that.ulElement.offsetWidth / 2) + 'px'; // that.ulElement的右边框与div的右边框对齐
                }
                that.ulElement.style.left = (that.ulElement.offsetLeft + speed) + 'px';
            }
        },

        mounted() {
            let that = this;
            this.timerId = setInterval(function() {
                that.move(-2)
            }, 30)
        },
        destroyed() {
            let that = this;
            clearInterval(that.timerId)
        },
        created() {},
        components: {},
        props: ['joinList']
    }
</script>


<style lang="scss" scoped>
    @mixin Hcenter {
        transform: translateX(-50%);
        left: 50%;
    } // 最新揭晓
    $avtar-size: 30px;
    $margin-top-bottom: 10px;
    $item-height: $avtar-size+2 * $margin-top-bottom;
    @keyframes movin {
        to {
            transform: translateX(-50%)
        }
    }
    .move {
        --animationMoveDuration: 120s;
        animation: movin var(--animationMoveDuration) linear infinite;
    }
    @keyframes movin-infinite {
        to {
            transform: translateX(50%)
        }
    }
    .movinInfinite {
        animation: movin-infinite linear;
    }
    .join {
        // background: #fff;
        height: $item-height;
        &-content {
            // margin: 0 5%;
            white-space: nowrap;
            overflow-x: scroll;
            overflow-y: hidden;
            height: $item-height;
            position: relative;
            &-wrap {
                // background: #fff;
                position: absolute;
                height: $item-height;
                z-index: 1;
            }
            &-item {
                background: rgba(0, 0, 0, 0.5);
                border-radius: 100px;
                height: $avtar-size;
                margin: $margin-top-bottom 20px $margin-top-bottom 0px;
                position: relative;
                display: inline-block;
                &:active {
                    opacity: 0.3;
                }
                &-img {
                    vertical-align: middle;
                    width: 0;
                    height: 0; // padding: 50px;
                    padding: $avtar-size / 2;
                    background: rgba(255, 255, 255, 0.829);
                    border-radius: 100px;
                    position: relative;
                    display: inline-block;
                    >img {
                        border-radius: 100px;
                        width: 100%;
                        height: 100%;
                        object-fit: cover;
                        position: absolute;
                        transform: translate(-50%, -50%);
                        left: 50%;
                        top: 50%;
                        border-radius: 100px;
                    }
                }
                &-txt {
                    font-size: 12px;
                    display: inline-block;
                    vertical-align: middle;
                    margin: 0 20px 0 10px;
                    line-height: $avtar-size;
                    .name {
                        color: rgb(255, 255, 255);
                    }
                    .num {
                        color: #F7134F;
                        margin: 0 5px;
                    }
                    .txt {
                        color: #333333;
                    }
                }
            }
        }
    }
</style>


<style>
    /* 滚动条样式修改 */
     ::-webkit-scrollbar {
        width: 1px;
        height: 1px;
        /* background-color: #fff; */
        background-color: transparent;
    }
    /*定义滚动条轨道 内阴影+圆角*/
     ::-webkit-scrollbar-track {
        /* -webkit-box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.1); */
        border-radius: 10px;
        /* background-color: rgba(255, 255, 255, 0.3); */
        background-color: transparent;
    }
    /*定义滑块 内阴影+圆角*/
     ::-webkit-scrollbar-thumb {
        border-radius: 10px;
        /* -webkit-box-shadow: inset 0 0 3px rgba(0, 0, 0, .15); */
        /* background-color: rgb(191, 203, 217) */
        /* background-color: #fff; */
        background-color: transparent;
    }
</style>
