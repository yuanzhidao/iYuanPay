<template>
    <a :href="props.value">
    <div class="flex justify-center items-center overflow-hidden mt-3">
    <VueQrcode 
        :value="props.value"
        :options="{
            color: {
                dark: props.bgColor,
                light: '#ffffff00',
            },
            width: '200'
        }" 
        tag="img"
    />
    </div>
    </a>
    
</template>

<script setup>
    import VueQrcode from '@chenfengyuan/vue-qrcode';
    const props = defineProps(['value','bgColor'])
</script>
