<template>
    <div id="nav">
        <router-link v-for="route in routes" :to="route.path" :key="route.path">{{ route.name }}&nbsp;&nbsp;</router-link>
    </div>
    <router-view />
</template>
<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import { routes } from './router';
@Options({
    data: () => ({
        routes,
    }),
})
export default class App extends Vue {}
</script>
<style lang="scss">
#nav {
    a {
        font-weight: bold;
        color: #2c3e50;
        text-decoration: none;

        &.router-link-exact-active {
            color: #42b983;
        }
    }
}
</style>
