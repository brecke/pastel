<script>
  import { Router, Route } from "svelte-navigator";
  import PrivateRoute from "./routes/PrivateRoute.svelte";

  import Homepage from "./routes/Homepage.svelte";
  import Dashboard from "./routes/Dashboard.svelte";
  import Library from "./routes/Library.svelte";
  import Groups from "./routes/Groups.svelte";
</script>

<Router>
  <Route useFocus path="/">
    <Homepage let:params let:location let:registerFocus />
  </Route>
  <Route path="/login">
    <Homepage goToLogin="true" let:params let:location let:registerFocus />
  </Route>
  <PrivateRoute path="dashboard" let:params let:location let:registerFocus>
    <Dashboard />
  </PrivateRoute>
  <PrivateRoute path="library" let:params let:location let:registerFocus>
    <Library />
  </PrivateRoute>
  <PrivateRoute path="groups" let:params let:location let:registerFocus>
    <Groups />
  </PrivateRoute>
</Router>
