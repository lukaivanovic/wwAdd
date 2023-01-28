<template>
    <div>
        <input class="search label-sm" placeholder="Search..."/>
    </div>
</template>

<style scoped>
    .search{
        height: 32px;
        width: 100%;
        background-color: var(--bg-secondary);
        border: none;
        padding: 0px 8px;
        border-radius: 6px;
        margin-top: 8px;
        margin-bottom: 8px;
    }

    .search:focus{
        color: var(--content-primary);
        outline-width: 0.5px;
    }
</style>