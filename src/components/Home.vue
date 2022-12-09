<template>
    <!-- Home Tab -->
    <div id="main" class="main-content">
        <section id="hometab" class="home">
            <div class="text">
                <h1 class="text-center">Xin chào,</h1>
                <p>Các chức năng bạn có thể thực hiện</p>
                <div class="box-card">
                    <div class="card">
                        <div class="card-body" style="font-size: 20px">
                            <h1 class="card-title">
                                Tra cứu thông tin học sinh
                            </h1>
                            <p class="card-text text-muted">
                                Tra cứu điểm TB học kì 1 và học kì 2 của học
                                sinh
                            </p>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-body" style="font-size: 20px">
                            <h1 class="card-title">Tiếp nhận học sinh</h1>
                            <p class="card-text text-muted">
                                Tiếp nhận học sinh mới theo quy định của nhà
                                trường
                            </p>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-body" style="font-size: 20px">
                            <h1 class="card-title">Lập danh sách lớp</h1>
                            <p class="card-text text-muted">
                                Lập danh sách lớp phù hợp với quy định của nhà
                                trường
                            </p>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-body" style="font-size: 20px">
                            <h1 class="card-title">Nhập bảng điểm môn học</h1>
                            <p class="card-text text-muted">
                                Nhập điểm 15', 1 tiết và cuối HK của học sinh
                                theo lớp, môn học và học kì
                            </p>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-body" style="font-size: 20px">
                            <h1 class="card-title">Lập báo cáo tổng kết</h1>
                            <p class="card-text text-muted">
                                Lập báo cáo tổng kết theo môn học, học kì
                            </p>
                        </div>
                    </div>
                </div>
                <div class="avatar">
                    <h1>Thông tin tài khoản</h1>
                    <h5>Giáo vụ</h5>
                    <div class="avt-img">
                        <img src="img/logo_small.png" alt="" />
                    </div>
                    <input type="file" id="myFile" name="Sửa" label="Sửa" />
                    <input type="button" id="change" value="Thay đổi" />
                    <input type="button" id="remove" value="Gỡ" />
                    <div class="input-group">
                        <label for="email">Email</label>
                        <input id="email" name="email" type="email" />
                        <label for="name">Tên</label>
                        <input id="name" type="text" />
                        <label for="phone">Số điện thoại</label>
                        <input id="phone" type="text" />
                        <!-- <label for="password">Mật khẩu</label>
                        <input id="password" type="password" /> -->
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
export default {
    name: 'HomeComponent',
    methods: {
        onSearch() {
            this.$tabName = 'Search';
            console.log(this.$tabName);
        },
    },
};
</script>

<style scoped>
.main-content {
    position: absolute;
    top: 0;
    left: 250px;
    height: 100vh;
    width: calc(100% - 250px);
    background-color: var(--body-color);
    transition: var(--tran-05);
}

.card {
    background-color: var(--body-color);
    transition: var(--tran-05);
    padding: 30px;
    margin: 15px;
    border: 2px solid var(--text-color);
    border-radius: 25px;
    height: 150px;
    width: 28rem;
}

.box-card {
    float: left;
}

.avatar h1,
h5 {
    text-align: center;
}

.input-group input {
    display: block;
    height: 40px;
    margin-bottom: 20px;
    width: 20vw;
    font-size: 25px;
    padding-left: 5px;
    color: var(--text-color);
    background-color: var(--body-color);
    border-color: 10px var(--body-color);
}

#remove {
    width: 50px;
    height: 30px;
    background-color: var(--remove-btn);
    border-radius: 5px;
}

#change {
    width: 100px;
    height: 30px;
    margin-right: 5px;
    background-color: var(--change-btn);
    border-radius: 5px;
}

.avt-img {
   text-align: center;
   margin: 10px;
}
#email {
    pointer-events: none;
}

.input-group {
    justify-content: center;
    margin-top: 15px;
}

.avatar img {
    width: 15rem;
    height: inherit;
    margin: auto;
    justify-content: center;
}

.input-group label {
    font-size: 20px;
}

.avatar {
    margin-left: 40vw;
}

.avatar input {
    font-size: 20px;
}

.main-content .text {
    font-size: 30px;
    font-weight: 500;
    padding: 15px 60px;
}

.main-content.close {
    left: 78px; /* Original: 78px */
    height: 100vh;
    width: calc(100% - 78px);
}

.main-content .text .card {
    color: var(--text-color);
}
</style>