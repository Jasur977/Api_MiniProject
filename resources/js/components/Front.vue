<template>
    <div class="container">
        <div class="row">
            <div class="col-lg-3">
                <h1 class="my-4">Shop Name</h1>
                <div class="list-group">

                    <a class="list-group-item" v-for="category in categories">
                        {{category.name}}

                    </a>

                </div>
            </div>
            <div class="col-lg-9">
                <div class="carousel slide my-4" id="carouselExampleIndicators" data-ride="carousel">
                    <ol class="carousel-indicators">
                        <li class="active" data-target="#carouselExampleIndicators" data-slide-to="0"></li>
                        <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
                        <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
                    </ol>
                    <div class="carousel-inner" role="listbox">
                        <div class="carousel-item active"><img class="d-block img-fluid"
                                                               src="https://via.placeholder.com/900x350"
                                                               alt="First slide"/></div>
                        <div class="carousel-item"><img class="d-block img-fluid"
                                                        src="https://via.placeholder.com/900x350" alt="Second slide"/>
                        </div>
                        <div class="carousel-item"><img class="d-block img-fluid"
                                                        src="https://via.placeholder.com/900x350" alt="Third slide"/>
                        </div>
                    </div>
                    <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
                        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                        <span class="sr-only">Previous</span>
                    </a>
                    <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
                        <span class="carousel-control-next-icon" aria-hidden="true"></span>
                        <span class="sr-only">Next</span>
                    </a>
                </div>

                <div class="row mt-4">
                    <div class="col-lg-4 col-md-6 mb-4" v-for="product in products">
                        <div class="card h-100">
                        <a href="#">
                            <img class="card-img-top" src="" alt="">
                        </a>
                        <div>
                            <div class="card-body">
                                <h4 class="card-title">
                                    <a href="#">{{product.name}}</a>
                                </h4>
                                <h5>$ {{product.price}}</h5>
                                <p class="card-text"> {{product.description}}</p>
                            </div>

                        </div>
                        </div>

                    </div>


                </div>

            </div>
        </div>
    </div>
</template>

<script>
export default {
    data: function (){
        return{
            categories: [],
            products: []
        }
    },
    mounted() {
        this.loadCategories();
        this.loadProducts();
    },
    methods:{
        loadCategories:function (){
            axios.get('/api/categories')
            .then((response) => {
                this.categories = response.data.data;

            })
            .catch(function (error){
                console.log(error);
            })

        },
        loadProducts:function (){
            axios.get('/api/products')
                .then((response) => {
                    this.products = response.data.data;

                })
                .catch(function (error){
                    console.log(error);
                })

        }
    }
}
</script>
