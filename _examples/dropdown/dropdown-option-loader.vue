<script setup>
async function loadCurrentlyPopularMovies({ page, hasNextPage }) {
  const res = await fetch(
    `https://api.themoviedb.org/3/movie/popular?api_key=f48bcc9ed9cbce41f6c28ea181b67e14&language=en-US&page=${page}`
  )
  if (res.ok) {
    const data = await res.json()
    if (page !== data.total_pages) hasNextPage()
    return data.results.map((item) => ({ label: item.title, value: item.id }))
  }
  return []
}

// The function assigned to the `option-loader` prop will be called with the
// value of the option as the first argument (in this case, the movie ID), and
// the cached option as the second argument (if it exists).
async function loadMovie(id, cachedOption) {
  if (cachedOption) return cachedOption
  const res = await fetch(
    `https://api.themoviedb.org/3/movie/${id}?api_key=f48bcc9ed9cbce41f6c28ea181b67e14&language=en-US`
  )
  if (res.ok) {
    const data = await res.json()
    return {
      label: data.title,
      value: data.id,
    }
  }
  return { label: 'Error loading' }
}
</script>

<template>
  <FormKit type="form" :actions="false">
    <FormKit
      type="dropdown"
      name="currentlyPopularMovie"
      label="Choose a currently popular movie"
      placeholder="Example placeholder"
      :options="loadCurrentlyPopularMovies"
      :option-loader="loadMovie"
      :value="597"
    />
  </FormKit>
</template>

<style>
.movie-review {
  white-space: pre-wrap;
}
</style>
