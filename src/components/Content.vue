<template>
    <main class="flex justify-center items-center">
        <div class="container flex justify-center items-center w-80 bg-white rounded-3xl shadow-2xl flex-col dark:bg-zinc-600">
            
            <QrcodeGenerator v-if="props.notWechat" :bg-color="props.bgColor" :value="props.qrValue"/>
            <img v-else :src="props.qrValue" alt="Wechat QR Code" style="width:200px;" class="m-6 rounded-3xl">

            <div class="flex justify-center items-center mb-7 mt-2">
                <div class="text-slate-700 dark:text-slate-200 flex justify-center items-center flex-col text-xs font-bold mr-4">
                    <div class="bg-slate-700 text-white rounded-full w-4 h-4 text-center mb-1">1</div><Qrcode /><div class="mt-1">长按保存图片</div>
                </div>
                <div class="text-slate-700 dark:text-slate-200 flex justify-center items-center flex-col text-xs font-bold mr-4">
                    <div class="bg-slate-700 text-white rounded-full w-4 h-4 text-center mb-1">2</div><Scan /><div class="mt-1">返回 App 扫描</div>
                </div>
                <div class="text-slate-700 dark:text-slate-200 flex justify-center items-center flex-col text-xs font-bold">
                    <div class="bg-slate-700 text-white rounded-full w-4 h-4 text-center mb-1">3</div><Success /><div class="mt-1">输入金额付款</div>
                </div>
            </div>

        </div>
    </main>
</template>

<script setup>
import QrcodeGenerator from './QrcodeGenerator.vue';
import Qrcode from '../assets/img/Qrcode.vue';
import Scan from '../assets/img/Scan.vue';
import Success from '../assets/img/Success.vue';

const props = defineProps(['bgColor','qrValue','notWechat'])
</script>