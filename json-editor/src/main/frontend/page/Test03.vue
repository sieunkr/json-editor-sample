<template>
    <div class="container">

        <h1>테스트03 - 필드 커스텀 설정</h1>
        <h4>Tree 입력 타입에서, Key(필드)를 수정하지 못하도록 설정 (원래는 Tree타입에서는 필드명도 수정 가능)</h4>

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
                schema: this.schema,
                modes: ['tree', 'form', 'view'],
                onChange: () => {
                    //
                },
                onEditable: function (node) {
                    switch (node.field) {
                        case 'name':
                            return false;
                        case 'born':
                            return {
                                field: false,
                                value: true
                            };
                        case 'job':
                            return {
                                field: false,
                                value: true
                            };
                        default:
                            return true;
                    }
                }
            };
            const editor = new JSONEditor(container, options);

            // JSON 기본 데이터
            let json = {
                "name": "Eddy.Kim",
                "born": 1981,
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