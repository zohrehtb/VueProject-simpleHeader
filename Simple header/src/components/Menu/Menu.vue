<template>
    <nav 
        v-if="items && items.length" 
        class="menu"
    >
        <ul>
            <li 
                v-for="(item, index) in items"
                :key="index"
                class="menu__item"
            >
                <a 
                    v-if="item.link" 
                    :href="item.link"
                >
                    <span 
                        v-if="item.icon"
                        class="material-icons"
                    >
                        {{item.icon}}
                    </span> 
                    {{item.title}}
                </a>
            </li>
        </ul>
    </nav>
</template>

<script>

    export default {
        name: 'mainMenu',

        props:{
            /**
             * list of menu
             */
            items: {
                type: Array,
            },
        }

    };
</script>
