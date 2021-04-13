<script>
  import { Router, Route } from "svelte-navigator";
  import Homepage from "./routes/Homepage.svelte";
  import Dashboard from "./routes/Dashboard.svelte";
  import Library from "./routes/Library.svelte";
  import Groups from "./routes/Groups.svelte";
</script>

<Router>
  <Route useFocus path="/" component={Homepage} />
  <Route path="dashboard" component={Dashboard} />
  <Route path="library" component={Library} />
  <Route path="groups" component={Groups} />
</Router>
