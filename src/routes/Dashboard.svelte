<script lang="ts">
  import anylogger from "anylogger";
  import "@polymer/iron-icons/iron-icons.js";
  import { useFocus } from "svelte-navigator";
  import { onMount } from "svelte";
  import { getCurrentUser, user } from "../stores/user";
  import {
    activities,
    processedActivities,
    fetchUserActivities,
  } from "../stores/activity";
  import NewsFeed from "../components/NewsFeed.svelte";
  import MainLayout from "../components/MainLayout.svelte";
  import { useLocation, useNavigate } from "svelte-navigator";

  const navigate = useNavigate();
  const location = useLocation();
  const log = anylogger("oae-dashboard");
  const registerFocus = useFocus();

  onMount(async () => {
    // TODO not sure why this is necessary, but I think it is
    user.set(await getCurrentUser());

    // TODO debug
    log.warn($user);

    activities.set(await fetchUserActivities());

    // TODO debug
    log.warn("Processed activities:");
    log.warn($processedActivities);
  });
</script>

<MainLayout>
  <div use:registerFocus>
    {#each $processedActivities as eachActivity (eachActivity.id)}
      <NewsFeed activityItem={eachActivity} />
    {/each}
  </div>
</MainLayout>

<style lang="scss">
  @import "../styles/buttons.scss";

  h3 {
    color: #212121;
    font-size: 14px;
  }

  .dashboard-icon {
    color: #212121;
    margin-right: 0.8em;
  }

  .content-dashboard {
    position: absolute;
  }

  .sidebar {
    height: 100%;
  }
</style>
