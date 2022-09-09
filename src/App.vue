<template >
  <div id="app">
    <div class="app vertical-nav bg-white" id="sidebar">
      <div class="py-4 px-3 mb-4 bg-light">
        <div class="media d-flex align-items-center">
          <div class="media-body">
            <h4 class="m-0">GRAS Anthony</h4>
            <p class="font-weight-light text-muted mb-0">Projet Spa</p>
          </div>
        </div>
      </div>

      <p class="text-gray font-weight-bold text-uppercase px-3 small pb-4 mb-0">Article</p>

      <ul class="nav flex-column bg-white mb-0">
        <li class="nav-item">
          <router-link to="/" class="nav-link text-dark font-italic ">
            <i class="fa fa-th-large mr-3 text-primary fa-fw"></i>
           Liste
          </router-link>
        </li>
      </ul>

    </div>
    <router-view/>
  </div>
</template>

<style scope>

#sidebar.active {
  margin-left: -17rem;
}

#content.active {
  width: 100%;
  margin: 0;
}

@media (max-width: 768px) {
  #sidebar {
    margin-left: -17rem;
  }
  #sidebar.active {
    margin-left: 0;
  }
  #content {
    width: 100%;
    margin: 0;
  }
  #content.active {
    margin-left: 17rem;
    width: calc(100% - 17rem);
  }
}

/*
*
* ==========================================
* FOR DEMO PURPOSE
* ==========================================
*
*/

#app {
  background: #c5bebe;
  background: -webkit-linear-gradient(to right, #398fc2, #d9cfcf);
  background: linear-gradient(to right, #6a8fcb, #7ad7cf);
  min-height: 100vh;
  overflow-x: hidden;
}



.text-uppercase {
  letter-spacing: 0.1em;
}

.text-gray {
  color: #aaa;
}
</style>

