<template>
  <!-- <div class="row section collapsible collapsed"> -->
<section class="unmaterialized">
  <h3>Downloaded Git Repos by Project</h3>

  <!--Add Search bar and Search button next to head 
  <div class="searchform">
      <form action="" class="...">
          <input type="text" class="search" placeholder="Search">
          <input type="button" name="Search" id="searchbutton" class="">
      </form>
  </div>
-->

  <!--Add sort dropdown and "Sort" button under search form-->
  <div class="sortForm">
  		<select id="sortSelect">
		  <option value="atoz">A to Z</option>
		  <option value="ztoa">Z to A</option>
		  <option value="totalcommits">Total Commits</option>
		</select>
		<button @click="sort">Sort</button>
  </div>

  <!--<div id="example">
    <input type="text" v-model="searchData" placeholder="Please put your key word here">
    <ul>
      <li v-for="(item,index) in Newitems" :key="index">
        <span>{{item.id}}</span>
        <span>{{item.name}}</span>
        <span>{{item.time}}</span>
      </li>
    </ul>
  </div>-->


  <div class="row section">
    <hr>
    <div style=" margin-left: 42.4%" class="col col-12 relative spinner loader"></div>
    <div v-for="project in projects" class="col-6">
      <h4 class="repoTitle">{{ project }}</h4>
        <div class="repo-link-holder">
          <table class="is-responsive">
            <thead class="repo-link-table repo-link-table-body">
              <tr>
                <th>URL</th>
		<th>Status</th>
                <th>Number of repos: {{ repos[project].length }}</th> <!-- change this to display the number of repos -->
              </tr>
            </thead>
            <tbody class="repo-link-table repo-link-table-body">
              <tr v-for="repo in repos[project]">
                <td><!-- <router-link :to="'git/' + (repo.url).slice(11)" @click.prevent="onGitRepo(repo)" class="repolink fade">{{ repo.url }}</router-link> --><!-- <a :href="'?git=' + btoa(repo.url)" class="repolink fade">{{ repo.url }}</a> -->
                  <a href="#" @click="onGitRepo(repo)">{{ repo.url }}</a>
                </td>
                <td>{{ repo.status }}</td> <!-- change this to display number of repos in the project -->
	        <td></td>
	       </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </section>
</template>

<script>

module.exports = {
  data () { return {
    repos: {},
    projects: []
  }},
  methods: {
    onRepo (e) {
      this.$store.commit('setRepo', {
        githubURL: e.target.value
      })
    },
    onGitRepo (e) {
      let first = e.url.indexOf(".")
      let last = e.url.lastIndexOf(".")
      let domain = null
      let owner = null
      let repo = null
      let extension = false

      if (first == last){ //normal github
        domain = e.url.substring(0, first)
        owner = e.url.substring(e.url.indexOf('/') + 1, e.url.lastIndexOf('/'))
        repo = e.url.slice(e.url.lastIndexOf('/') + 1)
      } else if (e.url.slice(last) == '.git'){ //github with extension
        domain = e.url.substring(0, first)
        extension = true
        owner = e.url.substring(e.url.indexOf('/') + 1, e.url.lastIndexOf('/'))
        repo = e.url.substring(e.url.lastIndexOf('/') + 1, e.url.length - 4)
      } else { //gluster
        domain = e.url.substring(first + 1, last)
        owner = null //e.url.substring(e.url.indexOf('/') + 1, e.url.lastIndexOf('/'))
        repo = e.url.slice(e.url.lastIndexOf('/') + 1)
      }
      this.$store.commit('setRepo', {
        gitURL: e.url
      })

      this.$store.commit('setTab', {
        tab: 'git'
      })

      this.$router.push({
        name: 'git',
        params: {repo: e.url}
      })
    },
    getDownloadedRepos() {
      this.downloadedRepos = []
      window.AugurAPI.getDownloadedGitRepos().then((data) => {
        $(this.$el).find('.spinner').removeClass('loader')
        $(this.$el).find('.spinner').removeClass('relative')
        this.repos = window._.groupBy(data, 'project_name')
        this.projects = Object.keys(this.repos)
      })
    },

	/*Add sort function to sort listed repos*/
	sort() {
		alert("hello");
	},

    /* Add Search Function to parse the projects array and return projects contains key words 
    getSearchRe(){
    	
    },*/
    
    

    /* Add function to get number of repos in a project
    getReposCount(){
      var count;
      for(object in repos){
	count = object.length;
    }
    */

    btoa(s) {
      return window.btoa(s)
    }
  },
  mounted() {
    this.getDownloadedRepos()
  } 
};


export default {
  name: "HelloWorld",
  data() {
    return {
      searchData: "",
      items: [
        { id: "1001", name: "哈哈", time: "20170207" },
        { id: "1002", name: "呵呵", time: "20170213" },
        { id: "1103", name: "晓丽", time: "20170304" },
        { id: "1104", name: "小兰", time: "20170112" },
        { id: "1205", name: "财务", time: "20170203" },
        { id: "1206", name: "嘻嘻", time: "20170208" },
        { id: "1307", name: "测试", time: "20170201" }
      ]
    };
  },
  computed: {
    Newitems() {
      var _this = this;
      var Newitems = [];
      _this.items.map(function(item) {
        if (
          item.id.search(_this.searchData) != -1 ||
          item.name.search(_this.searchData) != -1
        ) {
          Newitems.push(item);
        }
      });
      return Newitems;
    }
  }
};

    /* Add sort function to reorder displayed repos based on user-selected criteria
    sortRepos()
    {
    	
    }*/

</script>