<template>
  <div class="empty-groups">
    <div class="empty-groups__description">
      <div class="empty-groups__title">{{ $t("nothing_here") }}</div>
      <div class="empty-groups__content">
        {{ $t("empty_groups_description") }}
      </div>
    </div>
    <div class="empty-groups__guidance">
      <div class="empty-groups__title">{{ $t("any_students_yet") }}</div>
      <div class="empty-groups__button">
        <Button
          :label="$t('find_students')"
          type="cta"
          size="large"
          position="right"
          width="190px"
          height="48px"
          padding-top="16px"
          @click="findStudents"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Button from "~/components/ui/buttons/Button";

export default {
  name: "EmptyGroups",
  components: {
    Button,
  },
  methods: {
    findStudents() {
      console.log("Go to find students...");
    },
  },
};
</script>

<style lang="scss" scoped>
@import "/assets/scss/components/coach/empty-groups";
</style>
