<script setup>
import Header from './components/Header.vue';
import Content from './components/Content.vue';
import { ref } from 'vue';
import Footer from './components/Footer.vue';

function addDarkListen(event) {
    if (event.matches) {
        document.documentElement.classList.add('dark');
    } else {
        document.documentElement.classList.remove('dark');
    }
}

window.matchMedia('(prefers-color-scheme: dark)').addEventListener("change", (e) => {
    addDarkListen(e);
    ElMessage({
        message: '检测到您已切换系统主题。',
        type: 'warning',
        duration: 5000,
        customClass: 'rounded-3xl dark:bg-zinc-700',
    });
})

addDarkListen(window.matchMedia('(prefers-color-scheme: dark)'));

const bgColor = ref('#475569')

const qrValue = ref('')

const notWechat = ref(true);

const message = ref("请使用 支付宝/微信/QQ 扫码。");

if (navigator.userAgent.match(/Alipay/i)) {
    qrValue.value = 'https://qr.alipay.com/fkx164291ms97i3hrvqpp1f';
    message.value = '识别为 支付宝 页面。';
} else if (navigator.userAgent.match(/MicroMessenger\//i)) {
    qrValue.value = 'https://tvax3.sinaimg.cn/mw690/007kXifNly1gyvmzfmsnnj30ew0evtfu.jpg';
    notWechat.value = false;
    message.value = '识别为 微信 页面。';
} else if (navigator.userAgent.match(/QQ\//i)) {
    qrValue.value = 'https://i.qianbao.qq.com/wallet/sqrcode.htm?m=tenpay&f=wallet&a=1&ac=CAEQlczJYxiik4uPBg%3D%3D_xxx_sign&u=208823829&n=%E3%80%80';
    message.value = '识别为 QQ 页面。';
} else {
    qrValue.value = 'https://iyuanpay.vercel.app/'
}

if(document.documentElement.classList.contains('dark') == true){
    bgColor.value = '#e4e7ee';
}

ElMessage({
    message: message,
    type: 'warning',
    duration: 10000,
    customClass: 'rounded-3xl dark:bg-zinc-700',
    'show-close': true,
});
</script>

<template>
    <Header />
    <Content v-if="notWechat" :bg-color="bgColor" :qr-value="qrValue" :not-wechat="notWechat"/>
    <Content v-else :qr-value="qrValue" :not-wechat="notWechat"/>
    <Footer />
</template>
