<template>
    <div class="container">

        <h1>테스트01 - 스키마 설정</h1>


        <h5>입력 타입 : {{selectedEditorType}}</h5>

        <div id="jsoneditor" style="width: 400px; height: 400px;"></div>

    </div>
</template>

<script>
    import JSONEditor from 'jsoneditor';
    import 'jsoneditor/dist/jsoneditor.min.css';

    export default {
        data() {
            return {
                selectedEditorType: "",
                schema: {},
            }
        },
        mounted() {

            //스키마 설정
            this.schema = {
                "title": "person",
                "type": "object",
                "properties": {
                    "name": {
                        "type": "string"
                    },
                    "born": {
                        "type": "integer"
                    },
                    "gender": {
                        "enum": ["male", "female"]
                    },
                    "job": {
                        "type": "array",
                        "items": {
                            "properties": {
                                "name": {
                                    "type": "string"
                                },
                                "category": {
                                    "type": "string"
                                },
                            }
                        }
                    }
                },
                "required": ["name"]
            };

            // create the editor
            const container = document.getElementById("jsoneditor");
            let options = {};
            options = {
                schema: this.schema,
                modes: ['form','code','text', 'tree', 'view'], // 설정하지 않으면 tree 가 default, 순서대로 메뉴에 표시되는데 이 경우에는 form 타입
                onChange: () => {
                    //
                },
                onModeChange: (newMode, oldMode) => {
                //onModeChange: function (newMode, oldMode) {
                    this.selectedEditorType = newMode;
                }
            };
            const editor = new JSONEditor(container, options);

            // JSON 기본 데이터
            let json = {
                "name": null,
                "born": 0,
                gender: null,
                "job": []
            };
            editor.set(json);

        },
        computed: {
        },
        methods: {
        }
    };
</script>