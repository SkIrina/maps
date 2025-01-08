<template>
    <div>
        <p>pull-to-refresh / 引っ張って更新するのは禁止</p>
        <button @click="moveToNavigation">ナビ</button>
        <span>https://www.google.co.jp/maps/dir/?api=1&destination=35.487676,133.049012&travelmode=driving</span>
        <p @click="increment">クリック: {{ count }}</p>
        <p id="locations">{{ log }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            count: 0,
            log: ''
        }
    },
    mounted() {
        this.geoFindMe();
    },
    methods: {
        moveToNavigation() {
            this.increment()
            const fallbackUrl = `https://www.google.co.jp/maps/dir/?api=1&destination=35.487676,133.049012&travelmode=driving`;
            window.open(fallbackUrl, '_blank');
        },
        increment() {
            this.count++
        },
        geoFindMe() {
            if (!navigator.geolocation) {
                this.log += "ジオロケーションがブラウザでサポートされていません";
            } else {
                this.log += "位置情報を取得し、変更を追跡...\n";
                navigator.geolocation.watchPosition(this.success, this.error);
            }
        },
        success(position) {
            const latitude = position.coords.latitude;
            const longitude = position.coords.longitude;

            const now = new Date();
            this.log += `[${now.toLocaleTimeString('ja-JP')}] ${latitude}, ${longitude} \n`;
        },
        error(error) {
            this.log += `ERROR(${error.code}): ${error.message}`;
        }
    }
}
</script>

<style>
body {
    overscroll-behavior-y: contain;
}

button {
    padding-inline: 20px;
}

#locations {
    white-space: pre;
}
</style>