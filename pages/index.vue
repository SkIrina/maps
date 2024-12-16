<template>
    <div>
        <button @click="moveToNavigation">ナビ</button>
        <span>https://www.google.co.jp/maps/dir/?api=1&destination=35.487676,133.049012&travelmode=driving</span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            mountains: []
        }
    },
    methods: {
        moveToNavigation() {
            const fallbackUrl = `https://www.google.co.jp/maps/dir/?api=1&destination=35.487676,133.049012&travelmode=driving`;
            window.location.href = fallbackUrl;
        }
    }
}
</script>