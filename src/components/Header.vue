<script setup>
    const props = defineProps(['bgColor'])

</script>

<template>
    <header class="flex justify-center items-center">
        <div class="m-6 flex flex-nowrap justify-center items-center rounded-3xl shadow-2xl w-80 bg-white dark:bg-zinc-600">
            <img src="https://q4.qlogo.cn/headimg_dl?dst_uin=208823829&spec=640" alt="Avatar" class="w-14 mr-4 rounded-full my-3">
            <div class="py-4 font-bold text-3xl text-slate-600 dark:text-slate-200">
                iYuan Pay
            </div>
        </div>
    </header>
</template>