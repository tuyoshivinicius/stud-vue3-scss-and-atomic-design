<template>
  <div>
    <articles class="o-card">
      <div class="o-card__header">
        <h1 class="o-card__header__title">{{ title }}</h1>
        <div class="o-card__header__dropdown">
          <i class="fas fas-down" /><span>{{ dropDownLabel }}</span>
          <ul class="o-card__header__dropdown__menu">
            <li v-for="(item, i) in dropDownItems" :key="`dropmenu_item` + i">
              <a :href="item.link" class="o-card__header__dropdown__menu__item">
                {{ item.label }}
              </a>
            </li>
          </ul>
        </div>
      </div>
      <div class="o-card__body">{{ body }}</div>
      <div class="o-card__footer">
        <span class="o-card__header__dropdown__menu__date">
          {{ date.toLocaleDateString("pt-BR") }}
        </span>
        <span class="o-card__header__dropdown__menu__state">
          Satus:{{ status }}
        </span>
      </div>
    </articles>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    title: {
      type: String,
      default: "Titulo padrao",
    },
    dropDownLabel: {
      type: String,
      default: "Configurações",
    },
    dropDownItems: {
      type: Array,
      default: () => {
        return [
          {
            label: "Site do google",
            link: "https://google.com",
          },
          {
            label: "Site do uol",
            link: "https://uol.com",
          },
        ];
      },
    },
    body: {
      type: String,
      default: "Este é o corpo do card insira o conteudo aqui",
    },
    date: {
      type: Date,
      default: new Date(),
    },
    status: {
      type: Boolean,
      default: true,
    },
  },
};
</script>

<style lang="scss">
.o-card {
  $borderRadius: 20px;

  font-family: Arial, Helvetica, sans-serif;
  width: 100%;
  text-align: center;
  margin: 0 10px;

  &__header,
  &__body,
  &__footer {
    padding: 20px;
  }

  &__header {
    background-color: #EEE;
    border-radius: $borderRadius $borderRadius 0px 0px;

    > * {
      display: block;
    }

    &__title {
      font-size: 22px;
    }
    &__dropdown {
      background-color: #999;
      padding: 10px;
      cursor: pointer;

      &__menu {
        padding: 0;
        list-style: none;
        display: none;

        li {
        }
      }
      &:hover &__menu {
        display: block;
      }
    }
  }

  &__body {
    padding: 40px;
    background-color: #FFF;
  }

  &__footer {
    background-color: #EEE;
    border-radius: 0px 0px $borderRadius $borderRadius;
    > * {
      display: block;
    }
  }
}
</style>