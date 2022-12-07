<template>
    <!-- Search Tab -->
    <div id="main" class="main-content">
        <section id="searchtab" class="search">
            <div class="text">
                <h1>Tra cứu thông tin học sinh</h1>
                <h3>
                    Nhập vào tên học sinh hoặc mã số học sinh. Bạn có thể chọn
                    lớp ở nút phía dưới
                </h3>
            </div>
            <div class="search-container">
                <div class="input-box">
                    <input
                        type="text"
                        placeholder="Tên học sinh..."
                        spellcheck="false"
                    />
                    <span class="icon">
                        <i class="bx bx-search search-icon"></i>
                    </span>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
export default {
    name: 'SearchComponent'
}
</script>
<style>
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