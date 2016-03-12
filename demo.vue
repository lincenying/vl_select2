<style lang="less">

select,
input {
    outline: none;
}

</style>

<template>

<vl-select
    :data="list"
    :model.sync="model"
    :placeholder="placeholder"
    :allowclear="allowClear"
    :multiple="multiple"
    :tags="tags">
</vl-select>

</template>

<script>

import vlSelect from "./vl-select.vue";
export default {
    data() {
        return {
            list: [{
                id:1,
                text: "php"
            },{
                id:2,
                text: "nodejs"
            },{
                id:3,
                text: ".net"
            },{
                id:4,
                text: "java"
            }],
            model: "",
            multiple: true,
            tags: true,
            placeholder: "请选择你喜欢的语言",
            allowClear: true
        }
    },
    components: {
        vlSelect
    }
};

</script>
