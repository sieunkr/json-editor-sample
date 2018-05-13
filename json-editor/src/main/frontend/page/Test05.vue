<template>
    <div class="container">

        <h1>테스트05 - 커스텀 디자인</h1>

        <div id="jsoneditor" style="width: 1024px; height: 768px;"></div>

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
                modes: ['form','tree'],
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
<style>

    /* dark styling of the editor */
    div.jsoneditor,
    div.jsoneditor-menu {
        border-color: #4b4b4b;
    }
    div.jsoneditor-menu {
        background-color: #4b4b4b;
    }
    div.jsoneditor-tree,
    div.jsoneditor textarea.jsoneditor-text {
        background-color: #666666;
        color: #ffffff;
        alignment: center;
    }
    div.jsoneditor-field,
    div.jsoneditor-value {
        min-height: 50px;
        min-height: 30px;
        font-size: x-large;
        color: #ffffff;
    }
    table.jsoneditor-search div.jsoneditor-frame {
        background: #808080;
    }

    tr.jsoneditor-highlight,
    tr.jsoneditor-selected {
        background-color: #808080;
    }

    div.jsoneditor-field[contenteditable=true]:focus,
    div.jsoneditor-field[contenteditable=true]:hover,
    div.jsoneditor-value[contenteditable=true]:focus,
    div.jsoneditor-value[contenteditable=true]:hover,
    div.jsoneditor-field.jsoneditor-highlight,
    div.jsoneditor-value.jsoneditor-highlight {
        background-color: #808080;
        border-color: #808080;
    }

    div.jsoneditor-field.highlight-active,
    div.jsoneditor-field.highlight-active:focus,
    div.jsoneditor-field.highlight-active:hover,
    div.jsoneditor-value.highlight-active,
    div.jsoneditor-value.highlight-active:focus,
    div.jsoneditor-value.highlight-active:hover {
        background-color: #b1b1b1;
        border-color: #b1b1b1;
    }

    div.jsoneditor-tree button:focus {
        background-color: #868686;
    }

    /* coloring of JSON in tree mode */
    div.jsoneditor-readonly {
        color: #acacac;
    }
    div.jsoneditor td.jsoneditor-separator {
        color: #acacac;
    }
    div.jsoneditor-value.jsoneditor-string {
        color: #00ff88;
    }
    div.jsoneditor-value.jsoneditor-object,
    div.jsoneditor-value.jsoneditor-array {
        color: #bababa;
    }
    div.jsoneditor-value.jsoneditor-number {
        color: #ff4040;
    }
    div.jsoneditor-value.jsoneditor-boolean {
        color: #ff8048;
    }
    div.jsoneditor-value.jsoneditor-null {
        color: #49a7fc;
    }
    div.jsoneditor-value.jsoneditor-invalid {
        color: white;
    }



</style>