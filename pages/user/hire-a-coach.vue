<template>
  <div class="main-container">
    <div class="main-container__title">{{ $t("hire_a_coach") }}</div>
    <div class="main-container__info">{{ $t("find_coaches") }}</div>
    <SearchCoach class="view-margin-bottom-24" @coach-selected="addCoach" />
    <div class="main-container__info">
      {{
        $tc("selected_coaches", selectedCoaches.length, {
          count: selectedCoaches.length,
        })
      }}
    </div>
    <div v-for="coach in selectedCoaches" :key="coach">
      <InvitationCoachCard :coach="coach" @remove="removeCoach" />
    </div>

    <v-btn
      class="main-container__button button__with-icon"
      @click="sendRequests"
      >{{ $t("send_requests") }}</v-btn
    >
  </div>
</template>

<script>
import InvitationCoachCard from "~/components/coach/InvitationCoachCard";
import SearchCoach from "~/components/coach/SearchCoaches.vue";

export default {
  components: { InvitationCoachCard, SearchCoach },
  data() {
    return {
      selectedCoaches: [],
    };
  },
  methods: {
    removeCoach(id) {
      this.selectedCoaches = this.selectedCoaches.filter(
        (obj) => obj.id !== id
      );
    },
    addCoach(coach) {
      if (!this.selectedCoaches.includes(coach)) {
        this.selectedCoaches.push(coach);
      }
    },
    async sendRequests() {
      for (let i = 0; i < this.selectedCoaches.length; i++) {
        await this.$store.dispatch(
          "user/hireCoach",
          this.selectedCoaches[i].id
        );
      }
      this.$router.push(`/user/`);
      this.$toast.success(this.$t("coach_requests_sent"), {
        position: "bottom-center",
      });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/pages/coach/create-edit-group";
@import "~/assets/scss/components/ui/buttons/button";
</style>
