<template>
    <span>
        <span v-if="showLink">
            <router-link
                :to="{
                    name: 'detail',
                    params: {
                        resourceName: field.resourceName,
                        resourceId: field.belongsToId
                    }
                }"
                class="no-underline dim text-primary font-bold"
            >
                {{ field.value }}
            </router-link>
        </span>
        <span v-else>{{ field.value }}</span>
        <span v-else>&mdash;</span>
    </span>
</template>

<script>
export default {
    props: ["resourceName", "field"],

    computed: {
        showLink() {
            return this.field.value && !this.field.fallback && this.field.showLinkToResourceFromIndex
        },
    },
};
</script>
