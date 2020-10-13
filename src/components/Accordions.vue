<template>
    <div style="padding: 3em">
        <button @click="toggleAll(showAll)">{{ showAll ? "Collapse" : "Expand" }} All</button>
        <div v-for="(acc, i) in list" :key="i">
            <button @click="toggle(i)">{{ acc.show ? "Collapse" : "Expand" }}</button>
            {{ acc.name }} is {{ acc.show ? "opened" : "closed" }}
            <ul v-show="acc.show">
                <li>list item 1</li>
                <li>list item 2</li>
                <li>list item 3</li>
            </ul>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
    name: "Accordions",
    data() {
        return {
            showAll: false,
            list: [
                { name: "1st Accordion", show: false },
                { name: "2nd Accordion", show: false },
                { name: "3rd Accordion", show: false },
            ],
        };
    },
    methods: {
        toggle(i: number) {
            this.list[i].show = !this.list[i].show;
        },
        toggleAll(cur: boolean) {
            this.list = this.list.map((item) => Object.assign({}, item, { show: !cur }));
            this.showAll = !this.showAll;
        },
    },
});
</script>

<style>
ul {
    list-style: none;
}
</style>
