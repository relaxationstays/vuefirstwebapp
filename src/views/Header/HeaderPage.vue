<template>
    <div class="main">
        <div class="header">
            <div style="width:20%">
                <MenuSection :headerData="headerData" />
            </div>
            <div v-if="!isMobile" style="width:40%; margin-left: 5%">
                <InputHeaderField :headerData="headerData" />
            </div>
            <div style="width:40%">
                <RightButton :headerData="headerData" />
            </div>
        </div>
        <div v-if="isMobile" style="width:100%">
            <InputHeaderField :headerData="headerData" />
        </div>
    </div>
</template>
<script>
import RightButton from '@/components/Header/buttonRight.vue';
import headerData from '@/content/header/header';
import MenuSection from '@/components/Header/Menu.vue';
import InputHeaderField from '@/components/Header/InputHeaderField.vue';
export default {
    name: 'HeaderPage',
    components: {
        InputHeaderField,
        MenuSection,
        RightButton
    },
    data() {
        return {
            headerData,
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
.main {
    border-bottom: 1px solid #ccc;
    padding-bottom: 10px;
    width: 100%;
}

.header {
    background-color: white;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky;
    top: 0;
    z-index: 1000;
    /* Ensure it stays on top */
}
</style>
