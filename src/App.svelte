<script>
  import { Router, Link, Route } from "svelte-navigator";
  import Homepage from "./routes/Homepage.svelte";
  import Dashboard from "./routes/Dashboard.svelte";
  import Library from "./routes/Library.svelte";
  import Groups from "./routes/Groups.svelte";
</script>

<Router>
  <!-- <nav>
    <Link to="/">Homepage</Link>
    <Link to="dashboard">Dashboard</Link>
    <Link to="library">Library</Link>
    <Link to="groups">Groups</Link>
  </nav>
-->
  <div>
    <Route path="/">
      <Homepage />
    </Route>
    <Route path="dashboard" component={Dashboard} />
    <Route path="library" component={Library} />
    <Route path="groups" component={Groups} />
    <!--
      <Route path="blog/*">
        <Route path="/">
          <Blog />
        </Route>
        <Route path=":id" component={BlogPost} />
      </Route>
    -->
    <!--  
  <Route path="search/:query" let:params>
    <Search query={params.query} />
  </Route>
   -->
  </div>
</Router>
