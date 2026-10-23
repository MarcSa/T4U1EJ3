<script setup lang="ts">
import { ref } from 'vue';
import type { Movie } from '@/interfaces/movie.interface';

const inTheaters = ref(false);
const movies: Movie[] = [
    {
        id: 1,
        name: 'The Godfather',
        description:
            'The aging patriarch of an organized crime dynasty transfers control of his clandestine empire to his reluctant son.',
        image: 'https://m.media-amazon.com/images/M/MV5BM2MyNjYxNmUtYTAwNi00MTYxLWJmNWYtYzZlODY3ZTk3OTFlXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_FMjpg_UY1982_.jpg',
        rating: 4,
        genres: ['Crime', 'Drama'],
        inTheaters: false,
        year: 1972,
    },
    {
        id: 2,
        name: 'The Shawshank Redemption',
        description:
            'Two imprisoned men bond over a number of years, finding solace and eventual redemption through acts of common decency.',
        image: 'https://m.media-amazon.com/images/M/MV5BNDE3ODcxYzMtY2YzZC00NmNlLWJiNDMtZDViZWM2MzIxZDYwXkEyXkFqcGdeQXVyNjAwNDUxODI@._V1_FMjpg_UX1200_.jpg',
        rating: 4,
        genres: ['Drama'],
        inTheaters: true,
        year: 1994,
    },
    {
        id: 3,
        name: 'The Dark Knight',
        description:
            'When the menace known as the Joker wreaks havoc and chaos on the people of Gotham, Batman must accept one of the greatest psychological and physical tests of his ability to fight injustice.',
        image: 'https://m.media-amazon.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_FMjpg_UY2048_.jpg',
        rating: 3,
        genres: ['Action', 'Crime', 'Drama'],
        inTheaters: false,
        year: 2008,
    },
];

const displayedMoviesArray = ref<Movie[]>([]);

displayedMoviesArray.value = [...movies];
const inTheatersFilter = () => {
    inTheaters.value = !inTheaters.value;

    displayedMoviesArray.value = movies.filter((movie) => !inTheaters.value || movie.inTheaters);
};
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-12 p-3">
                <div
                    class="d-flex flex-column flex-md-row justify-content-between align-items-center pt-2"
                >
                    <div>
                        <button class="btn btn-primary mb-2" @click="inTheatersFilter()">
                            <span v-if="inTheaters">Mostrar todas</span
                            ><span v-if="!inTheaters">En cines</span>
                        </button>
                    </div>

                    <p class="mb-0 h-100 bg-white btn mb-2">
                        Mostrando un total de: {{ displayedMoviesArray.length }} peliculas
                    </p>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-12 col-md-4 mb-5" v-for="movie in displayedMoviesArray" :key="movie.id">
                <div class="card h-100">
                    <div class="card-body">
                        <h2>{{ movie.name }} ({{ movie.year }})</h2>
                        <div class="image-container">
                            <img :src="movie.image" :alt="movie.name" class="img-fluid" />
                        </div>
                        <p>{{ movie.description }}</p>
                        <p class="mb-0"><strong>Valoración:</strong> {{ movie.rating }}/5</p>
                    </div>
                    <div
                        class="card-footer pt-0 pb-3 bg-white d-flex flex-md-row justify-content-between align-items-center"
                    >
                        <div class="genres">
                            <span class="pe-1" v-for="genre in movie.genres" :key="genre"
                                >{{ genre }}
                            </span>
                        </div>
                        <div class="intheater btn btn-success" v-if="movie.inTheaters">
                            <p class="mb-0">En cines</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card-footer {
    border-top: none;
}
</style>
