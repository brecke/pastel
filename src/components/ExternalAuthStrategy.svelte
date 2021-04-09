<script lang="ts">
  import {
    getLoginRedirectUrl as getRedirectUrl,
    getInvitationInfo,
  } from "../helpers/utils";
  import anylogger from "anylogger";
  import { onMount } from "svelte";

  const log = anylogger("external-auth-strategy");

  export let name: string;
  export let id: string;
  export let url: string;
  export let icon: string;
  let redirectUrl: string;
  let invitationToken: string;
  let invitationEmail: string;

  onMount(async () => {
    redirectUrl = getRedirectUrl();

    // Variable that keeps track of the invitation info that is available in the page context, if any
    const invitationInfo = getInvitationInfo();
    invitationToken = invitationInfo.token;
    invitationEmail = invitationInfo.email;

    // TODO debug
    log.debug(`redirectUrl: ${redirectUrl}`);
    log.debug(`invitation info: ${invitationEmail} / ${invitationToken}`);
  });

  const submitForm = (e: Event) => {
    // TODO
    log.debug("Here I go, using external auth again...");
  };
</script>

<form on:submit|preventDefault={submitForm} action={url} method="POST">
  <input type="hidden" name="invitationToken" bind:value={invitationToken} />
  <input type="hidden" name="invitationEmail" bind:value={invitationEmail} />
  <input type="hidden" name="redirectUrl" bind:value={redirectUrl} />
  <a
    on:click={submitForm}
    href="/"
    class={`${id} button is-round signIn-button`}
  >
    <i class={icon} />{name}
  </a>
</form>
