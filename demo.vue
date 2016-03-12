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
    :ajax="ajax"
    :escapemarkup="escapeMarkup"
    :templateselection="templateSelection"
    :templateresult="templateResult">
</vl-select>

</template>

<script>

import vlSelect from "./vl-select.vue";
export default {
    data() {
        return {
            model: "",
            multiple: false,
            placeholder: "请选择",
            allowClear: true,
            ajax: {
                url: "https://api.github.com/search/repositories",
                dataType: 'json',
                delay: 250,
                data(params) {
                    return {
                        q: params.term
                    };
                },
                processResults(data, params) {
                    return {
                        results: data.items
                    };
                },
                cache: true
            },
            escapeMarkup(markup) { return markup; },
            templateSelection(repo) { return repo.full_name; },
            templateResult(repo) { return repo.full_name; }
        }
    },
    components: {
        vlSelect
    }
};

</script>
