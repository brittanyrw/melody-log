<template>
  <section class="hero">
    <header>
      <div class="overview">
        <h1>Melody Log</h1>
        <div class="overview-text">
          <p>Project to gather my favorite hip-hop songs from every country.</p>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptas
            animi ex voluptatum commodi voluptate harum laborum eligendi
            voluptatem? Culpa, officia necessitatibus expedita earum sequi
            doloribus iste recusandae blanditiis fugit ipsum!
          </p>
          <p class="portfolio-link">
            Created by
            <a href="https://musicalwebdev.com" target="_blank"
              >Brittany Walker.</a
            >
          </p>
        </div>
      </div>
      <div class="hero-sidebar">
        <div class="external-links">
          <h2>Other Logs</h2>
          <div class="links">
            <a href="https://theaterlog.com" target="_blank">Theater Log</a>
            <a href="https://thebookishlog.com" target="_blank">Bookish Log</a>
          </div>
        </div>
        <div class="info">
          <ul>
            <li>Some info here</li>
            <li>Some info here</li>
          </ul>
        </div>
      </div>
    </header>
    <div class="statistics">
      <div class="statistics-content">
        <h3>Statistics</h3>
        <div class="stats-wrapper">
          <div class="stats">
            <div class="counter total-stat">
              <p class="stat-number">123</p>
              <p class="stat-title">Total Stat Here</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    songs: Array,
  },
  computed: {
    viewedSongs() {
      return this.songs.filter((item) => item.title);
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/styles/variables.scss";
@import url("https://fonts.googleapis.com/css2?family=Abril+Fatface&display=swap");

.hero {
  header {
    border-bottom: 3px solid $black;
    @media screen and (min-width: 662px) {
      display: flex;
    }
    .overview {
      padding: 20px;
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      @media screen and (min-width: 662px) {
        flex-basis: 75%;
        border-right: 3px solid $black;
      }
      h1 {
        font-family: "Abril Fatface", cursive;
        margin: 0;
        letter-spacing: 1.5px;
        font-size: 40px;
      }
    }
    .hero-sidebar {
      @media screen and (min-width: 662px) {
        width: 300px;
      }

      .external-links,
      .info {
        padding: 20px;
      }

      .external-links {
        border-top: 3px solid $black;
        border-bottom: 3px solid $black;
        .links {
          display: flex;
          flex-wrap: wrap;
          justify-content: space-between;
          a {
            padding: 5px 10px;
            background-color: $black;
            color: $green;
            text-decoration: none;
            border: 3px solid $black;
          }
          a:hover {
            background-color: $green;
            color: $black;
            transition: 0.5s;
          }
        }
        @media screen and (min-width: 662px) {
          border-top: 0;
        }
      }

      .info {
        .fa-star {
          font-size: 24px;
        }
        .multi-example {
          border: 2px solid $black;
          padding: 5px;
          display: inline-block;
        }
        li:first-child {
          margin-bottom: 10px;
        }
        li {
          display: block;
        }
      }
    }
    .portfolio-link a {
      color: $black;
    }
  }
}

.statistics {
  border-bottom: 3px solid $black;
  .statistics-content {
    background-color: $black;
    color: $green;
    padding: 20px;
    h3 {
      margin: 0;
    }
    .stats {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-wrap: wrap;
      padding: 20px 0;
      @media screen and (min-width: 662px) {
        padding: 20px;
      }
      .counter {
        background-color: $green;
        text-align: center;
        margin: 10px;
        border: 2px solid $green;
        -webkit-box-shadow: 5px 5px 0 $green;
        box-shadow: 9px 9px 0 $green;
        border-radius: 7px;
        color: $black;
        outline: 3px solid $black;
        position: relative;
        .stat-number {
          font-size: 50px;
          font-weight: bold;
          margin: 0;
          padding: 10px 15px 0 15px;
        }
        .stat-title {
          margin: 0;
          padding: 0 15px 15px 15px;
        }
      }
    }
  }

  .review-legend {
    padding: 20px;
    border-top: 3px solid $black;
    text-align: center;
    .review-emoji-list {
      li {
        text-align: center;
        margin: 10px;
        .rating-name {
          border: 2px solid $black;
          padding: 5px 0 5px 5px;
          margin-bottom: 5px;
        }
        .rating-amount {
          padding: 5px;
          border-left: 2px solid $black;
          background-color: $black;
          color: $green;
        }
        img {
          width: 40px;
        }
      }
    }
  }
}
</style>
