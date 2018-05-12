<template>
    <div class="container">

        <h1>테스트04 - 자동 완성</h1>

        <div id="jsoneditor" style="width: 400px; height: 400px;"></div>

    </div>
</template>

<script>
    import JSONEditor from 'jsoneditor';
    import 'jsoneditor/dist/jsoneditor.min.css';

    export default {
        data() {
            return {
            }
        },
        mounted() {


            // create the editor
            const container = document.getElementById("jsoneditor");
            let options = {};
            options = {
                modes: ['tree', 'form', 'view'],
                onChange: () => {
                    //
                },
                autocomplete: {
                    getOptions: function () {
                        return ['developer','designer','testor']; //영문만 가능한 듯
                    }
                }
            };
            const editor = new JSONEditor(container, options);

            // JSON 기본 데이터
            let json = {
                "name": "Eddy.Kim",
                "born": 1981,
                "job": null
            };
            editor.set(json);

        },
        computed: {
        },
        methods: {
        }
    };
</script>