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
                    <router-link to="/"
                        ><li class="nav-link">
                            <label
                                @click="onHomeClick"
                                :class="
                                    currentTab === 'Home' ? 'current-nav' : ''
                                "
                            >
                                <i class="bx bx-home-alt icon"></i>
                                <span class="text nav-text">Home</span>
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
                    <router-link to="/admin">
                        <li class="nav-link">
                            <label
                                @click="onEditClick"
                                :class="
                                    currentTab === 'Edit' ? 'current-nav' : ''
                                "
                            >
                                <i class="bx bx-edit icon"></i>
                                <span class="text nav-text">Giáo vụ</span>
                            </label>
                        </li>
                    </router-link>
                    <!-- Quy định -->
                    <router-link to="/quy-dinh">
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
                                @click="onInfoClick"
                                :class="
                                    currentTab === 'Info' ? 'current-nav' : ''
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
let g_currentTab = 'Home';
export default {
    name: 'SideBar',
    data() {
        return {
            userName: g_userName,
            userType: g_userType,
            isDarkMode: g_isDarkMode,
            isNavClose: g_isNavClose,
            currentTab: g_currentTab,
        };
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
            g_currentTab = 'Login';
            alert('You are signed out');
            window.location.href = 'login.html';
        },
        onHomeClick() {
            g_currentTab = 'Home';
            this.currentTab = g_currentTab;
        },
        onSearchClick() {
            g_currentTab = 'Search';
            this.currentTab = g_currentTab;
        },
        onEditClick() {
            g_currentTab = 'Edit';
            this.currentTab = g_currentTab;
        },
        onRegulationClick() {
            g_currentTab = 'Regulation';
            this.currentTab = g_currentTab;
        },
        onInfoClick() {
            g_currentTab = 'Info';
            this.currentTab = g_currentTab;
        },
    },
};
</script>
<style>
/* Google Font Import - Poppins */
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@200;300;400;500;600;700&family=Kumar+One+Outline&display=swap');
@import url('https://unpkg.com/boxicons@2.1.1/css/boxicons.min.css');

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Josefin Sans', sans-serif;
}

:root {
    /* ===== Colors ===== */
    --body-color: #d3d4cd;
    --sidebar-color: #e8eae3;
    --primary-color: #fa2742;
    --hover-color: #80808080;
    --selected-hover-color: #f8546a;
    --text-color: #373833;

    /* ====== Transition ====== */
    --tran-03: all 0.2s ease;
    --tran-03: all 0.3s ease;
    --tran-04: all 0.3s ease;
    --tran-05: all 0.3s ease;
}

body {
    min-height: 100vh;
    background-color: var(--body-color);
    transition: var(--tran-05);
}

::selection {
    background-color: var(--primary-color);
    color: #fff;
}

body.dark {
    --body-color: #19212a;
    --sidebar-color: #1d2228;
    --primary-color: #fb8122;
    --hover-color: #80808080;
    --selected-hover-color: #f79951;
    --text-color: #e1e2e2;
}

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

/* search */
.search .text {
    margin-top: 20px;
    font-size: 30px;
    font-weight: 500;
    color: var(--text-color);
    padding: 12px 60px;
    text-align: center;
}

h3 {
    margin-top: 20px;
    font-size: 24px;
    font-weight: 200;
}

.search .input-box {
    position: relative;
    height: 65px;
    max-width: 70%;
    width: 100%;
    margin: 0 40px;
    border: 1px solid var(--text-color);
    border-radius: 10px;
    transition: all 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    padding: 0 15px 0 65px;
}

.search input {
    position: relative;
    outline: none;
    border: none;
    height: 100%;
    width: 100%;
    border-radius: 10px;
    font-size: 24px;
    font-weight: 400;
    color: var(--text-color);
    background-color: var(--body-color);
}

.search .icon {
    position: absolute;
    height: 100%;
    top: 0;
    left: 0;
    width: 60px;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    background-color: var(--body-color);
}

.search-container {
    margin-top: 50px;
    display: flex;
    justify-content: center;
}

.search .search-icon {
    position: absolute;
    top: 50%;
    font-size: 30px;
    transition: all 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.search .search-icon {
    color: var(--primary-color);
    transform: translateY(-50%) rotate(90deg);
}

.search .input-box .search-icon {
    transform: translateY(-50%) rotate(0);
}

.search .btn-group {
    margin-left: 100px;
}
</style>
