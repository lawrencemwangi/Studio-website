<script setup>
    import { ref, onMounted, onBeforeUnmount } from 'vue';

    const sections = ref([
    { id: 'Hero', label: 'Home', isActive: false },
    { id: 'About', label: 'About', isActive: false },
    { id: 'Music', label: 'Music', isActive: false },
    { id: 'Services', label: 'Services', isActive: false },
    { id: 'Gallery', label: 'Gallery', isActive: false },
    { id: 'Contact', label: 'Contact', isActive: false },

    ]);

    const isMenuOpen = ref(false);

    const navigate = (sectionId) => {
    const targetElement = document.getElementById(sectionId);
    if (targetElement) {
        window.scrollTo({
        top: targetElement.offsetTop,
        behavior: 'smooth',
        });
    }
    // Close the menu on navigation
    isMenuOpen.value = false;
    };

    const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
    };

    const updateActiveState = () => {
    const scrollPosition = window.scrollY;
    sections.value.forEach((section) => {
        const targetElement = document.getElementById(section.id);
        if (targetElement) {
        const offsetTop = targetElement.offsetTop;
        const offsetBottom = offsetTop + targetElement.offsetHeight;
        section.isActive = scrollPosition >= offsetTop && scrollPosition < offsetBottom;
        }
    });
    };

    onMounted(() => {
    updateActiveState();
    window.addEventListener('scroll', updateActiveState);
    });

    onBeforeUnmount(() => {
    window.removeEventListener('scroll', updateActiveState);
    });
</script>

<template>
    <div class="nav_container">
        <div class="logo">
            <img src="../assets/images/mic.jpg" width="50px" height="50px" alt="logo">
            <h2>Melody Mix Studio</h2>
        </div>

        <div class="nav_links">
            <ul :class="{ 'show-menu': isMenuOpen }">
                <li v-for="(section, index) in sections" :key="index" :class="{ active: section.isActive }">
                    <a @click.prevent="navigate(section.id)" href="#">{{ section.label }}</a>
                </li>
            </ul>
        </div>
        <div class="burger" @click="toggleMenu">
            <span :class="{ 'line-1': !isMenuOpen }"></span>
            <span :class="{ 'line-2': !isMenuOpen }"></span>
            <span :class="{ 'line-3': !isMenuOpen }"></span>
            
        </div>
    </div>
</template>