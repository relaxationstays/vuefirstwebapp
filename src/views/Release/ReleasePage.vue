<template>
    <div>
        <div class="header">
            <div :style="{ width: isMobile ? '100%' : '20%' }">
                <MenuSection :headerData="releaseData" :release="true" />
            </div>
        </div>
        <SongSection />
        <div :style="{ width: isMobile ? '100%' : '60%', marginTop: '30px' }">

            <SongSectionList />
        </div>
    </div>
</template>

<script>

import releaseData from '@/content/releases/Release';
import MenuSection from '@/components/Header/Menu.vue';
import SongSection from "@/components/Release/SongSection.vue";
import SongSectionList from "@/components/Release/SongSectionList.vue";

export default {
    name: 'ReleasePage',
    components: {
        MenuSection,
        SongSection,
        SongSectionList
    },
    data() {
        return {
            releaseData,
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
                this.menuOpen = false;
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
.header {
    /* background-color: #f8f8f8; */
    padding-top: 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>
