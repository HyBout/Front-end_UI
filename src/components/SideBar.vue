<template>
    <nav class="sidebar" :class="isNavClose ? 'close' : ''">
        <!-- Header: Group's name and Logo -->
        <header>
            <div class="image-text">
                <span class="image">
                    <img @mouseover="openNav" src="img/logo_small.png" alt="" />
                </span>
                <div class="text logo-text">
                    <span class="name"
                        >Nhóm <span class="groupname">14</span></span
                    >
                    <span class="profession">Quản lý học sinh</span>
                </div>
            </div>
            <i @click="closeNav" class="bx bx-chevron-right toggle"></i>
        </header>
        <!-- Menu bar -->
        <div class="menu-bar">
            <div class="menu">
                <!-- Home -->
                <ul class="menu-links">
                    <router-link to="/home"
                        ><li class="nav-link">
                            <label
                                @click="onHomeClick"
                                :class="
                                    currentTab === 'Home' ? 'current-nav' : ''
                                "
                            >
                                <i class="bx bx-home-alt icon"></i>
                                <span class="text nav-text">Trang chủ</span>
                            </label>
                        </li>
                    </router-link>
                    <!-- Tra cứu -->
                    <router-link to="/search">
                        <li class="nav-link">
                            <label
                                @click="onSearchClick"
                                :class="
                                    currentTab === 'Search' ? 'current-nav' : ''
                                "
                            >
                                <i class="bx bx-search-alt icon"></i>
                                <span class="text nav-text">Tra cứu</span>
                            </label>
                        </li>
                    </router-link>
                    <!-- Giáo vụ -->
                    <router-link to="/management">
                        <li class="nav-link">
                            <label
                                @click="onManagementClick"
                                :class="
                                    currentTab === 'Management' ? 'current-nav' : ''
                                "
                            >
                                <i class="bx bx-edit icon"></i>
                                <span class="text nav-text">Quản lý</span>
                            </label>
                        </li>
                    </router-link>
                    <!-- Quy định -->
                    <router-link to="/regulation">
                        <li class="nav-link">
                            <label
                                @click="onRegulationClick"
                                :class="
                                    currentTab === 'Regulation'
                                        ? 'current-nav'
                                        : ''
                                "
                            >
                                <i class="bx bx-key icon"></i>
                                <span class="text nav-text">Quy định</span>
                            </label>
                        </li>
                    </router-link>
                    <!-- Thông tin -->
                    <router-link to="/about">
                        <li class="nav-link">
                            <label
                                @click="onAboutClick"
                                :class="
                                    currentTab === 'About' ? 'current-nav' : ''
                                "
                            >
                                <i class="bx bx-info-circle icon"></i>
                                <span class="text nav-text">Thông tin</span>
                            </label>
                        </li>
                    </router-link>
                </ul>
            </div>

            <div class="bottom-content">
                <!-- Đăng xuất -->
                <li class="signout">
                    <label @click="onLogOut">
                        <i class="bx bx-log-out icon"></i>
                        <span class="text nav-text">Đăng xuất</span>
                    </label>
                </li>
                <!-- Dark/Light mode -->
                <li class="mode">
                    <div class="sun-moon">
                        <i class="bx bx-moon icon moon"></i>
                        <i class="bx bx-sun icon sun"></i>
                    </div>
                    <span class="mode-text text">{{
                        this.isDarkMode ? 'Chế độ sáng' : 'Chế độ tối'
                    }}</span>
                    <div @click="changeMode" class="toggle-switch">
                        <span class="switch"></span>
                    </div>
                </li>
            </div>
        </div>
    </nav>
</template>

<script>
const body = document.querySelector('body');
let g_userName = 'Phong Luu';
let g_userType = 2; // 0: chưa cấp quyền, 1: giáo viên, 2: giáo vụ, 3: quản trị viên.
let g_isDarkMode = true;
let g_isNavClose = false;

export default {
    name: 'SideBar',
    props: ['tabname'],
    data() {
        return {
            userName: g_userName,
            userType: g_userType,
            isDarkMode: g_isDarkMode,
            isNavClose: g_isNavClose,
            currentTab: 'Home',
        };
    },
    computed: {
        getTabName() {
            return 0;
        }
    },
    methods: {
        changeMode() {
            g_isDarkMode = !g_isDarkMode;
            this.isDarkMode = g_isDarkMode;
            body.classList.toggle('dark');
        },
        closeNav() {
            g_isNavClose = true;
            this.isNavClose = g_isNavClose;
            document.getElementById('main').className = 'main-content close';
        },
        openNav() {
            if (g_isNavClose) {
                g_isNavClose = false;
                this.isNavClose = g_isNavClose;
                document.getElementById('main').className = 'main-content';
            }
        },
        onLogOut() {
            g_userName = '';
            g_isDarkMode = true;
            g_isNavClose = false;
            this.$tabName = 'Login';
            alert('You are signed out');
            window.location.href = 'login.html';
        },
        onHomeClick() {
            this.currentTab = 'Home';
        },
        onSearchClick() {
            this.currentTab = 'Search';
        },
        onManagementClick() {
            this.currentTab = 'Management';
        },
        onRegulationClick() {
            this.currentTab = 'Regulation';
        },
        onAboutClick() {
            this.currentTab = 'About';
        },
    },
};
</script>
<style scoped>
/* ===== Sidebar ===== */
ul a {
    text-decoration: none;
}
.sidebar {
    position: fixed;
    top: 0;
    left: 0;
    height: 100%;
    width: 250px;
    padding: 10px 14px;
    background: var(--sidebar-color);
    transition: var(--tran-05);
    z-index: 100;
}

.sidebar.close {
    width: 88px;
}

/* ===== Reusable code - Here ===== */
.sidebar li {
    height: 50px;
    list-style: none;
    display: flex;
    align-items: center;
    margin-top: 10px;
}

.sidebar header .image,
.sidebar .icon {
    min-width: 60px;
    border-radius: 6px;
}

.sidebar .icon {
    min-width: 60px;
    border-radius: 6px;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
}

.sidebar .text,
.sidebar .icon {
    color: var(--text-color);
    transition: var(--tran-03);
}

.sidebar .text {
    font-size: 17px;
    font-weight: 500;
    white-space: nowrap;
    opacity: 1;
}

.sidebar.close .text {
    opacity: 0;
}

/* =========================== */

.sidebar header {
    position: relative;
}

.sidebar header .image-text {
    display: flex;
    align-items: center;
}

.sidebar header .logo-text {
    display: flex;
    flex-direction: column;
}

header .image-text .name {
    margin-top: 2px;
    font-size: 18px;
    font-weight: 600;
    padding-bottom: 5px;
}

header .image-text .groupname {
    font-family: 'Kumar One Outline', cursive;
}

header .image-text .name ::before {
    content: '';
    position: absolute;
    width: 20px;
    height: 20px;
    border-bottom: 4px solid var(--primary-color);
    border-left: 4px solid var(--primary-color);
    bottom: -3px;
    left: -2px;
}

header .image-text .name ::after {
    content: '';
    position: absolute;
    width: 20px;
    height: 20px;
    border-top: 4px solid var(--primary-color);
    border-right: 4px solid var(--primary-color);
    top: 0;
    right: 20px;
}

header .image-text .profession {
    font-size: 16px;
    margin-top: -2px;
    display: block;
}

.sidebar header .image {
    display: flex;
    align-items: center;
    justify-content: center;
}

.sidebar header .image img {
    width: 40px;
    border-radius: 6px;
}

.sidebar header .toggle {
    position: absolute;
    top: 50%;
    right: -25px;
    transform: translateY(-50%) rotate(180deg);
    height: 25px;
    width: 25px;
    background-color: var(--primary-color);
    color: var(--sidebar-color);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    cursor: pointer;
    transition: var(--tran-05);
}

body.dark .sidebar header .toggle {
    color: var(--text-color);
}

.sidebar.close .toggle {
    display: none;
}

.sidebar .menu {
    margin-top: 40px;
}

.sidebar li label {
    list-style: none;
    height: 100%;
    background-color: transparent;
    display: flex;
    align-items: center;
    height: 100%;
    width: 100%;
    border-radius: 6px;
    text-decoration: none;
    transition: var(--tran-03);
}

.sidebar li label:hover {
    background-color: var(--hover-color);
}

.sidebar li label:hover .icon,
.sidebar li label:hover .text {
    color: var(--sidebar-color);
}

body.dark .sidebar li label:hover .icon,
body.dark .sidebar li label:hover .text {
    color: var(--text-color);
}

.sidebar .menu-bar {
    height: calc(100% - 55px);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    overflow-y: scroll;
}

.menu-bar::-webkit-scrollbar {
    display: none;
}

.sidebar .menu-bar .mode {
    border-radius: 6px;
    position: relative;
    transition: var(--tran-05);
}

.menu-bar .mode .sun-moon {
    height: 50px;
    width: 60px;
}

.mode .sun-moon i {
    position: absolute;
}

.mode .sun-moon i.sun {
    opacity: 0;
}

body.dark .mode .sun-moon i.sun {
    opacity: 1;
}

body.dark .mode .sun-moon i.moon {
    opacity: 0;
}

.menu-bar .bottom-content .toggle-switch {
    position: absolute;
    right: 0;
    height: 100%;
    min-width: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 6px;
    cursor: pointer;
}

.toggle-switch .switch {
    position: relative;
    height: 22px;
    width: 40px;
    border-radius: 25px;
    background-color: var(--primary-color);
    transition: var(--tran-05);
}

.switch::before {
    content: '';
    position: absolute;
    height: 15px;
    width: 15px;
    border-radius: 50%;
    top: 50%;
    left: 5px;
    transform: translateY(-50%);
    background-color: var(--sidebar-color);
    transition: var(--tran-04);
}

body.dark .switch::before {
    left: 20px;
}

.sidebar .menu-bar .current-nav {
    border-radius: 6px;
    background-color: var(--primary-color);
}

.sidebar .menu-bar .current-nav span {
    color: white;
}

.sidebar .menu-bar .current-nav i {
    color: white;
}

.sidebar .menu-bar .current-nav:hover {
    background-color: var(--selected-hover-color);
}
</style>
