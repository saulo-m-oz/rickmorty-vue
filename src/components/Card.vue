<template>
    <div :class="status">
        <img :src="image" />
        <h1>{{name}}</h1>
    </div>
</template>

<script>
export default {
    props: ["image", "name", "status"]
}
</script>