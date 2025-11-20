<template>
  <div class="space-y-4">
    <Label class="mb-1 block">{{ t("templateSelector.title") }}</Label>
    <RadioGroup v-model="selectedTemplateIndex" class="grid grid-cols-2 gap-3 md:grid-cols-4">
      <label
        v-for="(template, index) in templates"
        :key="index"
        :for="`template-${index}`"
        class="relative flex cursor-pointer flex-col items-center space-y-2 rounded-md border-2 p-3 transition hover:opacity-80"
        :class="selectedTemplateIndexNumber === index ? 'border-primary' : 'border-transparent'"
      >
        <RadioGroupItem :id="`template-${index}`" :value="index.toString()" class="absolute top-3 right-3" />
        <img
          :src="template"
          :alt="t('templateSelector.templateAlt', { index: index + 1 })"
          class="max-h-16 w-full object-contain"
        />
        <span class="text-muted-foreground text-sm">
          {{ t("templateSelector.templateLabel", { index: index + 1 }) }}
        </span>
      </label>
    </RadioGroup>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from "vue";
import { useI18n } from "vue-i18n";
import { Label } from "@/components/ui";
import { RadioGroup, RadioGroupItem } from "@/components/ui/radio-group";

import template1 from "@assets/manga_templates/template-1.png";
import template2 from "@assets/manga_templates/template-2.png";
import template3 from "@assets/manga_templates/template-3.png";
import template4 from "@assets/manga_templates/template-4.png";

const { t } = useI18n();

const selectedTemplateIndex = ref("0");

const templates = [template1, template2, template3, template4];

const selectedTemplateIndexNumber = computed(() => Number(selectedTemplateIndex.value));
</script>

<style scoped></style>
