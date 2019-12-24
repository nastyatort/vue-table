<template>
<div class="main">
<Header></Header>
<Breadcrumbs></Breadcrumbs>
<Table></Table>
</div>
</template>


<script>
import Header from './Header.vue'
import Breadcrumbs from './Breadcrumbs.vue'
import Table from './Table.vue'

export default {
    name: 'Main',
    components: {
        Header,
        Breadcrumbs,
        Table
}
}
</script>