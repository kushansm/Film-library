<template>
  <section class="movie-grid">
    <div class="search-bar">
      <h2> Collect your favourites</h2>

      <input
          v-model="searchTerm"
          @input="searchMovies"
          placeholder="Search title and add to grid"
          class="search-input"
      />
    </div>


    <div class="grid">
      <div
          v-for="movie in movies"
          :key="movie.id"
          class="movie-card"
      >
        <img :src="movie.image" :alt="movie.title" />
        <h3>{{ movie.title }}</h3>
        <p>{{ movie.description }}</p>
        <button class="close-btn" @click="removeMovie(movie.id)">✖</button>
      </div>
    </div>
  </section>
</template>

<script>
import WildWest from '../assets/Wild West.jpg';
import Spiderman from '../assets/Spiderman.jpg';
import Batman from '../assets/Batman.jpg';

export default {
  name: 'VideoSection',
  data() {
    return {
      searchTerm: '',
      nextId: 4,
      movies: [
        {
          id: 1,
          title: 'Batman Returns',
          description: 'Lorem ipsum dolor sit amet,\n' +
              'consetetur sadipscing elitr, sed diam\n' +
              'nonumy eirmod tempor invidunt ut',
          image: Batman,
        },
        {
          id: 2,
          title: 'Wild Wild West',
          description: 'Lorem ipsum dolor sit amet,\n' +
              'consetetur sadipscing elitr, sed diam\n' +
              'nonumy eirmod tempor invidunt ut',
          image: WildWest,
        },
        {
          id: 3,
          title: 'The Amazing Spiderman',
          description: 'Lorem ipsum dolor sit amet,\n' +
              'consetetur sadipscing elitr, sed diam\n' +
              'nonumy eirmod tempor invidunt ut',
          image: Spiderman,
        },

      ],
    };
  },
  methods: {
    async searchMovies() {
      if (this.searchTerm.trim() === '') return;

      try {
        const res = await fetch(
            `https://api.tvmaze.com/search/shows?q=${this.searchTerm}`
        );
        const data = await res.json();

        if (data.length > 0) {
          const show = data[0].show;
          this.movies.push({
            id: this.nextId++,
            title: show.name,
            description:
                show.summary?.replace(/<[^>]*>/g, '') || 'No description available.',
            image:
                show.image?.medium ||
                'https://via.placeholder.com/210x295?text=No+Image',
          });
        }

        this.searchTerm = '';
      } catch (error) {
        console.error('Search failed:', error);
      }
    },
    removeMovie(id) {
      this.movies = this.movies.filter((m) => m.id !== id);
    },
  },
};
</script>

<style scoped>

.search-bar {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 2rem;
}

.search-bar h2 {
  font-size: 2rem;
  margin: 0;
  color: white;
}

.search-input {
  padding: 0.5rem;
  font-size: 1rem;
  flex-grow: 1;
  max-width: 400px;
  border: none;
  border-radius: 4px;
}

.movie-grid {
  color: white;
  background-color: #111;
  min-height: 100vh;
  padding-left: 7vw;
  padding-right: 7vw;
}

.movie-grid h2 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
}

.search-input {
  padding: 0.5rem;
  font-size: 1rem;
  margin-bottom: 2rem;
  width: 100%;
  max-width: 400px;
  border: none;
  border-radius: 4px;
}

.grid {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 1rem;
;
}

.movie-card {
  background-color: #222;
  border-radius: 8px;
  padding: 0rem;
  width: 31%;
  position: relative;
  box-shadow: 0 0 5px #000;
}

.movie-card img {
  width: 100%;
  height: 80%;
  border-radius: 4px;
  margin-bottom: 0.5rem;
  display: block;
  margin-left: 0;
  margin-right: 0;
}

.movie-card h3 {
  margin: 0.5rem 0 0.25rem;
}

.movie-card p {
  font-size: 0.9rem;
  color: #ccc;
}

.close-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  background: #e00;
  color: white;
  border: none;
  border-radius: 4px;
  font-size: 1rem;
  cursor: pointer;
}
</style>
