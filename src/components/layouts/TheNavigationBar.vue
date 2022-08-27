<template>
    <nav :class="'navbar white-bg fixed-top p-3 ' + navBarVisibility">
        <div class="container-fluid">
            <a class="navbar-brand" href="https://www.goldmansachs.com/" target="_blank" rel="noopener noreferrer">
            <img src="../../assets/icon.png" alt="">
            </a>
            <button
                class="navbar-toggler"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="#main-nav"
                aria-controls="main-nav"
                aria-expanded="false"
                aria-label="Toggle-navigation"
            >
                <span class="navbar-toggler-icon"></span>
            </button>
        </div>

        <!-- Nav bar links -->
        <div class="collapse navbar-collapse justify-content-start align-center ml-auto " id="main-nav">
            <ul class="navbar-nav text-nowrap">
                <li class="nav-item">
                    <a href="#about" class="nav-link">Dashboard</a>
                </li>
                <li class="nav-item">
                    <a href="#consumers" class="nav-link">Consumers</a>
                </li>
                <li class="nav-item">
                    <a href="#transactions" class="nav-link">Transactions</a>
                </li>
                <li class="nav-item">
                    <a href="#shops" class="nav-link">Shops</a>
                </li>
            </ul>
        </div>
    </nav>
</template>

<script>
import { reactive, toRefs, onMounted, computed } from 'vue';

export default {
    setup() {
        // Check for scrolling
        const state = reactive({
            lastScrollPosition: 0,
            showNavBar: true
        });

        const onScroll = () => {
            const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop;
            if (currentScrollPosition < 0) {
                return;
            }
            // Stop executing this function if the difference between
            // current scroll position and last scroll position is less than some offset
            if (Math.abs(currentScrollPosition - state.lastScrollPosition) < 60) {
                return;
            }
            state.showNavBar = currentScrollPosition < state.lastScrollPosition;
            state.lastScrollPosition = currentScrollPosition;
        };

        // If scrolling down, close else open
        const navBarVisibility = computed(() => {
            if (state.showNavBar) {
                return 'scrolled-up';
            }
            return 'scrolled-down';
        });

        onMounted(() => {
            console.log('mounted');
            window.addEventListener('scroll', onScroll);
        });

        return { ...toRefs(state), navBarVisibility };
    },

    name: 'NavigationBar'
};
</script>

<style scoped>
.scrolled-down {
    transform: translateY(-100%);
    transition: all 0.3s ease-in-out;
}
.scrolled-up {
    transform: translateY(0);
    transition: all 0.3s ease-in-out;
}

img {
    width: 108px;
}

</style>
