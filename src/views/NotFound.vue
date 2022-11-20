<template>
    <div className="m-3">
        <h3>The route does not exist</h3>
        <p>Request path : {{fullPath}}</p>
    </div>
</template>

<script>
import { useRoute } from 'vue-router';

export default {
    setup() {
        const route = useRoute();
        const fullPath  = route.fullPath
        return { fullPath };
    }
}
</script>

<style>

</style>