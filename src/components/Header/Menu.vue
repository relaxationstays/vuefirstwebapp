<template>
    <div class="menu">
        <div v-if="!release && isMobile" class="showmobile">
            <i class="fas fa-bars icon" @click="toggleMenu"></i>
        </div>
        <div>
            <h3 v-if="release" class="menu-title">Release</h3>
            <ul v-if="release" class="desktop-menu">
                <li class="list" v-for="(item, index) in headerData.menu" :key="item.title"
                    :style="{ backgroundColor: release && index === 0 ? '#f1c232' : '', textAlign: release ? 'center' : 'left' }">
                    {{ item.title }}
                </li>
            </ul>
            <ul v-if="!release && !isMobile" class="desktop-menu">
                <li class="list" v-for="(item, index) in headerData.menu" :key="item.title"
                    :style="{ backgroundColor: release && index === 0 ? '#f1c232' : '', textAlign: release ? 'center' : 'left' }">
                    {{ item.title }}
                </li>
            </ul>
        </div>
        <div :class="['side-menu', { 'menu-open': menuOpen }]">
            <ul>
                <li v-for="(item) in headerData.menu" :key="item.title" class="menu-item">
                    {{ item.title }}
                </li>
            </ul>
            <button class="close-btn" @click="toggleMenu">Close</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MenuSection',
    props: {
        headerData: {
            type: Object,
            required: true,
        },
        release: {
            type: Boolean,
            default: false,
        },
    },
    data() {
        return {
            isMobile: window.innerWidth <= 768,
            menuOpen: false,
        };
    },
    methods: {
        toggleMenu() {
            this.menuOpen = !this.menuOpen;
        },
        handleResize() {
            this.isMobile = window.innerWidth <= 768;
            if (!this.isMobile) {
                this.menuOpen = false; // Reset menu state for desktop
            }
        },
    },
    mounted() {
        window.addEventListener("resize", this.handleResize);
    },
    beforeUnmount() {
        window.removeEventListener("resize", this.handleResize);
    },
};
</script>

<style scoped>
.menu {
    position: relative;
    padding: 10px;
}

.menu-title {
    /* padding-left: 12%; */
    font-family: "Montserrat", serif !important;
}

.desktop-menu {
    display: flex;
    justify-content: space-around;
    list-style: none;
    padding: 0;
}

.list {
    padding: 10px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
    font-weight: 500;
    color: #333;
    transition: all 0.3s;
    width: 60%;
    margin-right: 10px;
    font-family: "Montserrat", serif !important;
}

.list:hover {
    background-color: #f4f4f4;
}

.showmobile .icon {
    font-size: 24px;
    cursor: pointer;
}

.side-menu {
    position: fixed;
    top: 0;
    right: 0;
    width: 250px;
    height: 100%;
    background-color: #333;
    color: white;
    padding: 20px;
    box-shadow: -2px 0 5px rgba(0, 0, 0, 0.5);
    transform: translateX(100%);
    transition: transform 0.3s ease-in-out;
    z-index: 100;
    font-family: "Montserrat", serif !important;
}

.side-menu.menu-open {
    transform: translateX(0);
}

.side-menu ul {
    list-style: none;
    padding: 0;
}

.menu-item {
    padding: 10px 0;
    border-bottom: 1px solid #444;
    cursor: pointer;
}

.menu-item:hover {
    background-color: #555;
}

.close-btn {
    margin-top: 20px;
    padding: 10px 20px;
    background-color: #f1c232;
    color: black;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-weight: bold;
    width: 100%;
}

.close-btn:hover {
    background-color: #d4a320;
}
</style>
