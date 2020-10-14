<template>
    <div style="padding: 24px">
        <!-- 一括開閉ボタン -->
        <button @click="toggleAll()">{{ showAll ? "Collapse" : "Expand" }} All</button>
        <!-- アコーディオンのデータリストをv-forで順番に展開する -->
        <!-- listからacc(アコーディオン)とi(インデックス)を同時に取り出す -->
        <div v-for="(acc, i) in list" :key="i">
            <!-- クリックイベントでtoggleにアコーディオンのインデックスを渡して開閉する -->
            <button @click="toggle(i)">{{ acc.show ? "Collapse" : "Expand" }}</button>
            {{ acc.name }} is {{ acc.show ? "opened" : "closed" }}
            <!-- show変数で表示・非表示 -->
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
            // 一括開閉の状態
            showAll: false,
            // アコーディオンのリスト
            list: [
                { name: "1st Accordion", show: false },
                { name: "2nd Accordion", show: false },
                { name: "3rd Accordion", show: false },
            ],
        };
    },
    methods: {
        // アコーディオンのインデックスを受け取って開閉する
        toggle(i: number) {
            this.list[i].show = !this.list[i].show;
        },
        // リスト内の全てのshowを!showAllに置き換えて一括開閉する
        // showAllを切り替える
        toggleAll() {
            this.list = this.list.map((item) => Object.assign({}, item, { show: !this.showAll }));
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
