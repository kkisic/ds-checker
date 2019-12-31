<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <input
        class="form-control mr-sm-2"
        type="search"
        placeholder="101, 102, ..., etc"
        aria-label="Search"
      />
      <button class="btn btn-outline-success my-2 my-sm-0">Not Started</button>
      <button class="btn btn-outline-success my-2 my-sm-0">In Progress</button>
      <button class="btn btn-outline-success my-2 my-sm-0">Done</button>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar"
};
</script>
