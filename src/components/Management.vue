<template>
    <!-- Insert Student Tab -->
    <div id="main" class="main-content">
        <div class="nav-group">
            <a href=""><i class="bx bx-user-circle"></i> Tiếp nhận học sinh</a>
            <a href=""><i class="bx bx-layer"></i> Lập danh sách lớp</a>
            <a href=""><i class="bx bxs-keyboard"></i> Nhập bảng điểm</a>
            <a href=""><i class="bx bxs-file-doc"></i>Lập báo cáo</a>
        </div>
        <div class="title">
            <span>Đã chọn</span>
            <div class="btn-group">
                <button id="remove">Xoá học sinh</button>
                <button id="change">Hoàn tất sửa đổi</button>
            </div>
        </div>
        <div class="info-table">
            <table>
                <tr>
                    <td><label>Họ và tên</label><input type="text" /></td>
                    <td><label>Email</label><input type="text" /></td>
                    <td><label>Giới tính</label><input type="text" /></td>
                </tr>
                <tr>
                    <td><label>Lớp</label><input type="text" /></td>
                    <td><label>Ngày sinh</label><input type="date" /></td>
                    <td><label>Số điện thoại</label><input type="text" /></td>
                </tr>
                <tr>
                    <td colspan="3"><label>Địa chỉ</label><textarea id="address" type="text"></textarea></td>
                </tr>
            </table>
        </div>
    </div>

    <!-- Create Classes Tab -->
    <!-- <div id="main" class="main-content">
        <div class="nav-group">
            <a href=""><i class="bx bx-user-circle"></i> Tiếp nhận học sinh</a>
            <a href=""><i class="bx bx-layer"></i> Lập danh sách lớp</a>
            <a href=""><i class="bx bxs-keyboard"></i> Nhập bảng điểm</a>
            <a href=""><i class="bx bxs-file-doc"></i>Lập báo cáo</a>
        </div>
        <div class="class-list">
            <div class="class-select">
                <span>Danh sách lớp</span>
                <select name="class">
                    <option value="10A1">10A1</option>
                    <option value="11A2">11A2</option>
                    <option value="12A3">12A3</option>
                </select>
            </div>
            <div class="btn-group">
                <button id="remove">Xoá lớp</button>
                <button id="change">Hoàn tất sửa đổi</button>
            </div>
        </div>
        <div class="insert-table">
            <table id="table-std">
                <thead>
                    <th>Tên</th>
                    <th>Lớp</th>
                    <th>Giới tính</th>
                    <th></th>
                </thead>
                <tbody>
                    <tr>
                        <td>ABC</td>
                        <td>10A1</td>
                        <td>Nam</td>
                        <td><button id="remove">Xoá khỏi lớp</button></td>
                    </tr>
                    <tr>
                        <td>XYZ</td>
                        <td>11A1</td>
                        <td>Nữ</td>
                        <td><button id="remove">Xoá khỏi lớp</button></td>
                    </tr>
                    <tr>
                        <td>DEF</td>
                        <td>12A1</td>
                        <td>Nam</td>
                        <td><button id="remove">Xoá khỏi lớp</button></td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="search-insert">
            <div class="search-insert-title">
                <span>Tìm kiếm học sinh</span>
                <div class="search-input">
                    <input
                        id="input-search"
                        type="text"
                        placeholder="Nhập tên học sinh ..."
                    />
                    <label for="input-search"
                        ><button><i class="bx bx-search"></i></button
                    ></label>
                </div>
            </div>
            <div class="insert-table">
                <table id="table-std">
                    <thead>
                        <th>Tên</th>
                        <th>Lớp</th>
                        <th>Giới tính</th>
                        <th></th>
                    </thead>
                    <tbody>
                        <tr>
                            <td>ABC</td>
                            <td>10A1</td>
                            <td>Nam</td>
                            <td><button id="change">Thêm vào lớp</button></td>
                        </tr>
                        <tr>
                            <td>XYZ</td>
                            <td>11A1</td>
                            <td>Nữ</td>
                            <td><button id="change">Thêm vào lớp</button></td>
                        </tr>
                        <tr>
                            <td>DEF</td>
                            <td>12A1</td>
                            <td>Nam</td>
                            <td><button id="change">Thêm vào lớp</button></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div> -->
</template>
<script>
export default {
    name: 'ManagementComponent',
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
    margin: auto;
}

.main-content.close {
    left: 78px;
    height: 100vh;
    width: calc(100% - 78px);
}

.main-content .text {
    color: var(--text-color);
}

/* CSS for tab */
.nav-group {
    display: flex;
    justify-content: center;
    margin-top: 40px;
}

.nav-group a {
    text-decoration: none;
    color: var(--text-color);
    font-size: 25px;
    padding: 10px;
    opacity: 0.75;
    border-radius: 10px;
    transition: var(--tran-03);
    margin: 0 10px;
}
.nav-group a:hover {
    background-color: var(--primary-color);
    color: var(--text-color);
    border-radius: 10px;
    opacity: 1;
}

/* CSS for Insert student tab */
.title {
    display: flex;
    justify-content: space-around;
    margin-top: 55px;
}

.btn-group button {
    max-width: 200px;
    height: 40px;
    margin: 0 10px;
    border-radius: 15px;
    font-size: 20px;
    padding: 5px;
    cursor: pointer;
    border: 0;
    color: var(--text-color);
}

.title span {
    font-size: 28px;
    color: var(--text-color);
    padding: 10px;
}

.btn-group #remove {
    background-color: var(--remove-btn);
}
.btn-group #change {
    background-color: var(--change-btn);
}

.info-table {
    display: flex;
    justify-content: center;
    margin-top: 40px;
}

.info-table table {
    border-spacing: 40px;
    border: 2px solid var(--text-color);
    border-radius: 25px;
}

.info-table table label {
    color: var(--text-color);
    font-size: 23px;
}

.info-table table input {
    height: 30px;
    max-width: 300px;
    width: 100%;
    font-size: 20px;
    border-radius: 8px;
    padding: 10px;
    border: 0;
}

.info-table table #address {
    width: 600px;
    margin-bottom: -25px;
    margin-left: 5px;
    font-size: 20px;
    height: 50px;
    border-radius: 8px;
    padding: 10px;
    border: 0;
}

/* CSS for Create classes tab */
.class-list {
    display: flex;
    justify-content: space-evenly;
    margin: 55px -150px 0 -150px;
}
.class-list span {
    font-size: 28px;
    color: var(--primary-color);
    font-weight: 900;
    padding: 0 10px;
    line-height: 15px;
}

.class-list select {
    width: 70px;
    height: 30px;
    font-size: 20px;
}

.insert-table {
    display: flex;
    justify-content: center;
    margin-top: 40px;
}

#table-std {
    border-spacing: 40px;
    border: 2px solid var(--text-color);
    border-radius: 25px;
}

#table-std th {
    font-size: 25px;
    font-weight: 900;
    padding: 5px 50px;
    color: var(--primary-color);
}

#table-std td {
    font-size: 20px;
    padding: 5px 50px;
    color: var(--text-color);
}

.search-insert-title {
    display: flex;
    justify-content: space-evenly;
    margin-top: 55px;
}
.search-insert-title span {
    font-size: 28px;
    color: var(--primary-color);
    padding: 0 10px;
    font-weight: 900;
}

.search-insert-title input {
    height: 30px;
    width: 350px;
    font-size: 20px;
    border-radius: 8px;
    padding: 10px;
    border: 0;
}
.search-insert-title button {
    background-color: var(--primary-color);
    height: 30px;
    width: 50px;
    font-size: 20px;
    border-radius: 8px;
    border: 0;
    margin: 5px;
}

#table-std td button {
    max-width: 200px;
    height: 40px;
    margin: 0 10px;
    border-radius: 15px;
    font-size: 20px;
    padding: 5px;
    cursor: pointer;
    border: 0;
    color: var(--text-color);
}

#table-std td #remove {
    border: 2px solid var(--remove-btn);
    color: var(--remove-btn);
}

#table-std td #remove:hover {
    background-color: var(--remove-btn);
    transition: var(--tran-03);
    color: var(--text-color);
}

#table-std td #change {
    border: 2px solid var(--change-btn);
    color: var(--change-btn);
}

#table-std td #change:hover {
    background-color: var(--change-btn);
    transition: var(--tran-03);
    color: var(--text-color);
}

</style>
