<template>
    <div>
        <div class="qr-container" id="donate">
            <vue-qr :text="qrUrl" v-bind="qrDefault" :colorDark="colorDark" :logoSrc="logoSrc" :bgSrc="bgSrc" v-show="isShow"></vue-qr>
        </div>
        <div class="menu"> 
            <circle-menu :number="number" :type="type" :animate="animate" circle :colors="['#E55652', '#5CB750', '#00A8F1', '#5294D0', '#009CE3']">
                <a slot="item_btn" class="icon icon-dashang" herf="#" @click="isShow=!isShow"></a>
                <a slot="item_1" class="icon icon-wechat" @click="alertQrcode('wechat')"></a>
                <a slot="item_2" class="icon icon-alipay" @click="alertQrcode('alipay')"></a>
                <a slot="item_3" class="icon icon-qq" @click="alertQrcode('qq')"></a>
                <a slot="item_4" class="icon icon-paypal" :href="paypalUrl"></a>
            </circle-menu>
        </div>
    </div>
</template>

<script>
import VueQr from 'vue-qr';
import CircleMenu from 'vue-circle-menu';
import 'animate.css';
export default {
    components: {
        VueQr,
        CircleMenu,
    },
    props: {
        number: {
            type: Number,
            required: true,
            validator: function (value) {
                return value > 1 && value < 5
            }
        },
        type: {
            type: String,
            required: true
        },
        animate: {
            type: String,
            default: "animated jello"
        },
        wechatpayUrl: {
            type: String
        },
        alipayUrl: {
            type: String
        },
        qqpayUrl: {
            type: String
        },
        paypalUrl: {
            type: String
        },
        colorDark: {
             type: String,
             default: "#000"
        },
        logoSrc: {
            type: String
        }, 
        bgSrc: {
            type: String,
        },
    },
    data(){
        return {
            qrDefault: {
                correctLevel: 3,
                size: 400,
                dotScale: 1,
                autoColor: true
            },
            qrUrl: "",
            isShow: false
        }
    },
    methods:{
        alertQrcode(donateType){
            if(this.bgSrc) {
                this.qrDefault.dotScale = 0.35;
            }
            this.isShow = true;
            switch (donateType) {
                case "qq":
                    this.qrUrl = this.qqpayUrl;
                    break;
                case "wechat":
                    this.qrUrl = this.wechatpayUrl;
                    break;
                case "alipay":
                    this.qrUrl = this.alipayUrl
                    break;
                default:
                    break;
            }
        }
    }
}
</script>

<style scoped>
    * {
        padding: 0;
        margin: 0;
        font-size: 0;
    }
    @font-face {
        font-family: 'icon-vue-donate';  /* project id 1368810 */
        src: url('./icons/iconfont.eot');
        src: url('./icons/iconfont.eot?#iefix') format('embedded-opentype'),
        url('./icons/iconfont.woff2') format('woff2'),
        url('./icons/iconfont.woff') format('woff'),
        url('./icons/iconfont.ttf') format('truetype'),
        url('./icons/iconfont.svg#iconfont') format('svg');
    }
    .icon {
        font-family: 'icon-vue-donate' !important;
        font-size: 30px;
        font-style: normal;
        color: #ffffff;
    }
    .icon-dashang::before {
        content: "\e691";
    }
    .icon-wechat::before {
        content: "\e65f";
    }
    .icon-alipay::before {
        content: "\e717";
    }
    .icon-qq::before {
        content: "\e663";
    }
    .icon-paypal::before {
        content: "\e824";
    }
    a {
        text-decoration: none;   
    }
    a:hover {
        cursor: pointer;
    }
    .qr-container {
        position: fixed;
        top: 3rem;
        left: 50%;
        transform: translate(-50%);
        z-index: 5200;
    }
    img {
        border-radius: 20px;
        width: 100%;
    }
</style>
