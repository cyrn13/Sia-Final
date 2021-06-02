<template>
    <div>
        <div v-if="get!=null">
            <h2 style="text-align:center;">{{get.title}}</h2><br><br>
            <div>
                
                <h3>{{get.category}}</h3><br>
            </div>
            <div>
                <p>{{get.description}}</p>
                <h4>${{get.price}}</h4>
            </div>
            <button style="float:right;" class="btn btn-success btn-sm"> Add to Cart</button>
            
        </div>
    </div>
</template>

<script>
export default {
    props: {
        get: null
    }
}
</script>

<style scoped>

</style>