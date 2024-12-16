<template>
    <div>
        <button @click="moveToNavigation">ナビ</button>
        <span>https://www.google.co.jp/maps/dir/?api=1&destination=35.487676,133.049012&travelmode=driving</span>
        <p @click="increment">クリック: {{ count }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            count: 0
        }
    },
    methods: {
        moveToNavigation() {
            this.increment()
            const fallbackUrl = `https://www.google.co.jp/maps/dir/?api=1&destination=35.487676,133.049012&travelmode=driving`;
            window.location.href = fallbackUrl;
        },
        increment() {
            this.count++
        }
    }
}
</script>

<style>
button {
    padding-inline: 20px;
}
</style>