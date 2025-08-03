<template>
  <section class="movie-grid">
    <div class="search-bar">
      <h2>Collect your favourites</h2>

      <input
          v-model="searchTerm"
          @input="searchMovies"
          placeholder="Search title and add to grid"
          class="search-input"
      />
    </div>

    <hr />

    <div class="grid">
      <div v-for="movie in movies" :key="movie.id" class="movie-card">
        <img :src="movie.image" :alt="movie.title" />
        <div class="card-content">
          <h3>{{ movie.title }}</h3>
          <p>{{ movie.description }}</p>
        </div>

        <button class="close-btn" @click="removeMovie(movie.id)">
          <img src="../../src/assets/Close White.svg" alt="Close" />
        </button>
      </div>
    </div>
  </section>
</template>

<script>
import WildWest from "../assets/Wild West.jpg";
import Spiderman from "../assets/Spiderman.jpg";
import Batman from "../assets/Batman.jpg";

export default {
  name: "VideoSection",
  data() {
    return {
      searchTerm: "",
      nextId: 4,
      movies: [
        {
          id: 1,
          title: "Batman Returns",
          description:
              "Lorem ipsum dolor sit amet, " +
              "consectetur adipiscing elit. Praesent " +
              "nec ligula eu lorem hendrerit hendrerit. " +
              "Cras eget est non felis consectetur fringilla." +
              " Suspendisse potenti. Morbi finibus turpis" +
              " sit amet justo tincidunt, a efficitur purus " +
              "porttitor. Etiam commodo felis eu magna fermentum," +
              " sed tincidunt leo dapibus.",
          image: Batman,
        },
        {
          id: 2,
          title: "Wild Wild West",
          description:
              "Lorem ipsum dolor sit amet, " +
              "consectetur adipiscing elit. Praesent " +
              "nec ligula eu lorem hendrerit hendrerit. " +
              "Cras eget est non felis consectetur fringilla." +
              " Suspendisse potenti. Morbi finibus turpis" +
              " sit amet justo tincidunt, a efficitur purus " +
              "porttitor. Etiam commodo felis eu magna fermentum," +
              " sed tincidunt leo dapibus.",
          image: WildWest,
        },
        {
          id: 3,
          title: "The Amazing Spiderman",
          description:
              "Lorem ipsum dolor sit amet, " +
              "consectetur adipiscing elit. Praesent " +
              "nec ligula eu lorem hendrerit hendrerit. " +
              "Cras eget est non felis consectetur fringilla." +
              " Suspendisse potenti. Morbi finibus turpis" +
              " sit amet justo tincidunt, a efficitur purus " +
              "porttitor. Etiam commodo felis eu magna fermentum," +
              " sed tincidunt leo dapibus.",
          image: Spiderman,
        },
      ],
    };
  },
  methods: {
    async searchMovies() {
      if (this.searchTerm.trim() === "") return;

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
                show.summary?.replace(/<[^>]*>/g, "") ||
                "No description available.",
            image:
                show.image?.medium ||
                "https://via.placeholder.com/210x295?text=No+Image",
          });
        }

        this.searchTerm = "";
      } catch (error) {
        console.error("Search failed:", error);
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
  color: white;
  margin-top: 4vh;
  flex: 1;
  min-width: 200px;
  word-break: break-word;
}
@media (max-width: 1024px) {
  .search-bar h2 {
    font-size: 1.75rem;
    margin-top: 2vh;
  }
}
@media (max-width: 600px) {
  .search-bar h2 {
    font-size: 1.5rem !important;
    margin-top: 1vh;
    width: 100%;
    text-align: left;
  }
}

.search-input {
  padding: 0.5rem;
  font-size: 1rem;
  flex-grow: 1;
  min-width: 200px;
  border: none;
  border-radius: 4px;
}

@media (max-width: 1024px) {
  .search-bar {
    flex-direction: row;
    justify-content: space-between;
  }

  .search-bar h2 {
    font-size: 1.75rem;
  }

  .search-input {
    max-width: 300px;
  }
}

@media (max-width: 600px) {
  .search-bar {
    flex-direction: column;
    align-items: flex-start;
  }

  .search-bar h2 {
    font-size: 1.5rem;
    width: 100%;
  }

  .search-input {
    width: 100%;
    max-width: 100%;
  }
}

.movie-grid {
  color: white;
  background-color: #111111;
  min-height: 100vh;
  padding-left: 7vw;
  padding-right: 7vw;
}

.movie-grid h2 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
}

.search-input {
  padding: 0.5rem 0.5rem 0.5rem 2.5rem;
  font-size: 1rem;
  width: 80%;
  max-width: 400px;
  border: none;
  border-radius: 4px;
  background-color: transparent;
  background-image: url("../../src/assets/Search White.svg");
  background-repeat: no-repeat;
  background-position: 0.5rem center;
  background-size: 20px 20px;
  color: white;
  border: 1px solid rgba(255, 255, 255, 0.3);
}

.search-input::placeholder {
  color: rgba(255, 255, 255, 0.5);
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  padding-top:2vh;
}

@media (max-width: 1024px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .grid {
    grid-template-columns: 1fr;
  }
}

.movie-card {
  background-color: #222;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 0 5px #000;
  display: flex;
  flex-direction: column;
  position: relative;
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
.card-content {
  padding: 1rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.card-content p {
  font-size: 0.9rem;
  color: #ccc;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 3; /* number of visible lines */
  -webkit-box-orient: vertical;
  text-overflow: ellipsis;
}

.close-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  background: rgb(64, 56, 56);
  border: none;
  cursor: pointer;
  padding: 8px;
  z-index: 2;
}

.close-btn img {
  width: 20px;
  height: 20px;
  display: block;
}
</style>