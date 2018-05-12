<template>
    <div>

        <router-link to="/test01">테스트1 - 스키마 설정</router-link>
        <br/>
        <router-link to="/test02">테스트2 - 템플릿</router-link>
        <br/>
        <router-link to="/test03">테스트3 - 필드 커스텀 설정</router-link>
        <br/>
        <router-link to="/test04">테스트4 - 자동 완성</router-link>

        <hr/>
        <!-- Page Content -->
        <div class="container">

            <router-view></router-view>

        </div>
    </div>
</template>

<script>
    import "bootstrap/dist/css/bootstrap.min.css";
    export default {
    };
</script>