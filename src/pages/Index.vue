<template>
  <Layout>
    <div class="row text-center">
      <h2 class="font-size-700 text-center fw-bold mb-3">Give us your email and we’ll give you our stories.</h2>
      <template>
        <mailchimp-subscribe
          url="https://siefertfamily.us7.list-manage.com/subscribe/post-json"
          user-id="a7630d1d6791ce52dccabb2dc"
          list-id="72a1272d4c"
          @error="onError"
          @success="onSuccess"
        >
          <template v-slot="{ subscribe, setEmail, error, success, loading }">
            <form @submit.prevent="subscribe">
              <div class="row g-2 mb-7 d-flex justify-content-center">
                <div class="col-md-6">
                  <div class="form-floating">
                    <input type="email" class="form-control form-control-lg" id="floatingInputValue" placeholder="email@domain.com" @input="setEmail($event.target.value)" />
                    <label for="floatingInputValue">Your Email</label>
                  </div>
                </div>
                <div class="col-md-2 d-grid">
                  <button type="submit" class="btn btn-xl btn-success mb-3">Submit</button>
                </div>
                <div v-if="error">
                  <div v-html="error"></div>
                  <!-- {{ error }} -->
                </div>
                <div v-if="success">Yay!</div>
                <div v-if="loading">Loading…</div>
              </div>
            </form>
          </template>
        </mailchimp-subscribe>
      </template>
    </div>
    
    <div class="row mx-sm-6">
      <div class="col text-center">
        <img src="@/assets/images/residents-brad.png" class="avatar mb-2" width="80" height="80" alt="Illustration avatar for Brad">
        <h3 class="font-size-900 fw-black font-secondary">Brad</h3>
      </div>
      <div class="col text-center">
        <img src="@/assets/images/residents-nic.png" class="avatar mb-2" width="80" height="80" alt="Illustration avatar for Nic">
        <h3 class="font-size-900 fw-black font-secondary">Nic</h3>
      </div>
      <div class="col text-center">
        <img src="@/assets/images/residents-steph.png" class="avatar mb-2" width="80" height="80" alt="Illustration avatar for Steph">
        <h3 class="font-size-900 fw-black font-secondary">Steph</h3>
      </div>
      <div class="col text-center">
        <img src="@/assets/images/residents-lydia.png" class="avatar mb-2" width="80" height="80" alt="Illustration avatar for Lydia">
        <h3 class="font-size-900 fw-black font-secondary">Lydia</h3>
      </div>
      <div class="col text-center">
        <img src="@/assets/images/residents-ringle.png" class="avatar mb-2" width="80" height="80" alt="Illustration avatar for Ringle">
        <h3 class="font-size-900 fw-black font-secondary">Ringle</h3>
      </div>
    </div>
    
  </Layout>
</template>

<script>
import MailchimpSubscribe from 'vue-mailchimp-subscribe'

export default {
  metaInfo: {
    title: 'A family newsletter from The Sieferts.'
  },
  components: {
    MailchimpSubscribe,
  },
  methods: {
    onError() {
      // handle error
      console.log('Error!');
    },
    onSuccess() {
      // handle success
      console.log('Success!');
      window.location.href = "/success";
    },
  },
}
</script>