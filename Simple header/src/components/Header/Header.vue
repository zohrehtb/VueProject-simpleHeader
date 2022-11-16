<template>
    <header class="main-header">
        <div class="container">
            <div class="main-header__inner">
                <div class="main-header__logo">
                    <img
                        :src="require('../../assets/logo.png')"
                        class="logo"
                        alt="Vue"
                    >
                </div>
                <c-menu
                    class="main-header__menu"
                    :items="menuList"
                />
                <div class="main-header__search">
                     <input
                        v-model="search"
                        type="text"
                        placeholder="Search..."
                    >
                </div>
            </div>
        </div>
    </header>
</template>

<script>
    import CMenu from '../Menu/Menu.vue'

    export default {
        name: 'mainHeader',

        components: {
           CMenu
        },

        /**
         * @inheritDoc
         */
        data() {
            return {
                showSearch: false,
                search    : null,
                menuList:[
                    {
                        title:'Home',
                        link:'#',
                        icon:'home'
                    },
                    {
                        title:'Blog',
                        link:'#',
                        icon:'border_color'
                    },
                    {
                        title:'News',
                        link:'#',
                        icon:'newspaper'
                    },
                    {
                        title:'products',
                        link:'#',
                        icon:'shopping_cart'
                    },
                    {
                        title:'contact us',
                        link:'#',
                        icon:'call'
                    },
                    {
                        title:'Login',
                        link:'#',
                        icon:'person'
                    },
                ]
            };
        },

        watch: {
            /**
             * Change parameters f route changes
             */
            $route() {
                this.showSearch = false;
                this.search = null;
            },
        },

        /**
         * @inheritDoc
         */
        created() {
            window.addEventListener('scroll', this.handleScroll);
        },

        /**
         * @inheritDoc
         */
        destroyed() {
            window.removeEventListener('scroll', this.handleScroll);
        },
        
        methods: {

            /**
             *  add class to menu in scroll page and remove it
             */
            handleScroll() {
                const header = document.querySelector('.main-header');
                if (window.scrollY > 10 && !header.className.includes('fixed')) {
                    header.classList.add('fixed');
                } else if (window.scrollY < 10) {
                    header.classList.remove('fixed');
                }
            },

            /**
           * Menu toggle
           */
            menuToggle() {
                this.isMenuOpen = !this.isMenuOpen;
                document.querySelector('.menu-wrapper')
                    .classList.toggle('mobile-nav-open');
            },
        },
    };
</script>
