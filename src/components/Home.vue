<template>
    <!-- Home Tab -->
    <div id="main" class="main-content">
        <section id="hometab" class="home">
            <div class="text">
                <h1>Xin chào</h1>
                <p>Bạn đang đăng nhập với quyền</p>
                <p>Bạn có thể</p>
            </div>
        </section>
    </div>
</template>

<script>
export default {
    name: 'HomeComponent',
};
</script>

<style scoped>
.main-content {
    position: absolute;
    top: 0;
    top: 0;
    left: 250px;
    height: 100vh;
    width: calc(100% - 250px);
    background-color: var(--body-color);
    transition: var(--tran-05);
}

.main-content .text {
    font-size: 30px;
    font-weight: 500;
    padding: 12px 60px;
}

.main-content.close {
    left: 78px;
    height: 100vh;
    width: calc(100% - 78px);
}

body.dark .main-content .text {
    color: var(--text-color);
}
</style>
