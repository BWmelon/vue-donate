<template>
    <div id="vue-app">
        <div class="demo">
            <donate :number="number" :type="type" :wechatpayUrl="wechatpay" :alipayUrl="alipay" :qqpayUrl="qqpay" :paypalUrl="paypal" :colorDark="colorDark" :logoSrc="logoSrc" :bgSrc="bgSrc"></donate>
        </div>
        
    </div>
</template>

<script>
import Donate from "./Donate";
export default {
    components: {
        Donate
    },
    data(){
        return {
            number: 4,
            type: "middle-around",
            wechatpay: "wxp://f2f0HzednLUZw5VTtEAadDk58_ch5vchrOy-",
            alipay: "HTTPS://QR.ALIPAY.COM/FKX09236UPGQ9V65UIQZCA",
            qqpay: "https://i.qianbao.qq.com/wallet/sqrcode.htm?m=tenpay&f=wallet&a=1&ac=CAEQl4jHtQUYz93y6AU%3D_xxx_sign&u=1454490647&n=%E6%89%93%EF%BC%8C%E6%89%93%E4%B8%AA%E5%A4%A7%E8%A5%BF%E7%93%9C%E3%80%80",
            paypal: "https://paypal.me/bwmelon?locale.x=zh_XC",
            colorDark: "#f00",
            logoSrc: "https://secure.gravatar.com/avatar/25c31bb2d1632ef016c7af2f67491593?s=220&r=X&d=mm",
            bgSrc: "https://imgs.bwmelon.com/20190811205536.png"
        }
    }
    
}

</script>

<style>
    body {
        background-color: #aa0000;
    }
    .demo {
        position: absolute;
        bottom: 3%;
        left: calc(50% - 24px);
    }
</style>

