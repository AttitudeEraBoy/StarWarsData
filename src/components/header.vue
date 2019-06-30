<template>
<div>
    <img alt="" src="http://www.playtcg.co.za/wp-content/uploads/2017/10/star-wars-banner-home.jpg" height="300px" class="img-fluid">
    <nav>
        <ul>
            <li><router-link to="/informs" exact>Characters</router-link></li>
            <li><router-link to="/movies" exact>Movies</router-link></li>
        </ul>
    </nav>
    </div>
</template>

<script>
export default {
    
}
</script>

<style scoped>
ul{
    list-style-type: none;
    text-align: center;
    margin: 0;
}
li{
    display: inline-block;
    margin: 0 10px;
}
a{
    color:#fff;
    text-decoration: none;
    padding: 6px 8px;
    border-radius: 10px;
}
nav{
    background: #444;
    padding: 14px 0;
    margin-bottom: 40px;
}
.router-link-active{
    background: #eee;
    color: #444;
}
</style>