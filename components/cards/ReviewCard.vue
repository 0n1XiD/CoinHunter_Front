<template>
    <div class="review-card">
        <div class="review-card__user">
            <div class="icon">
                <img
                    width="44"
                    height="44"
                    src="@/assets/img/user1.jpg"
                    alt="user1"
                >
            </div>
            <div class="name">
                Алексеев Алексей
            </div>
        </div>
        <div class="review-card__rating">
            <svg-icon
                v-for="(star, starIndex) in 5"
                :key="`star-${starIndex}`"
                icon="star"
                :fill="getStarColor(star)"
            />
        </div>
        <div class="review-card__review">
            CoinHunter превзошел мои ожидания! Он точно определил оптимальные
            варианты для моего бизнеса, сэкономив время и ресурсы.
            Рекомендую всем предпринимателям!
        </div>
    </div>
</template>

<script setup>
const rating = ref(4)

const getStarColor = (starNum) => {
  if (starNum <= rating.value) { return '#FFFFFF' }
  return '#6E6E8A'
}
</script>

<style lang="scss" scoped>
.review-card{
    width: 420px;
    height: 404px;
    padding: 36px;
    background: var(--bg-dark-blue);
    border-radius: 32px;
    &__user{
        margin-bottom: 6px;
        display: flex;
        align-items: center;
        .icon{
            margin-right: 12px;
            width: 44px;
            height: 44px;
            border-radius: 100%;
            overflow: hidden;
            img{
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }
        .name{
            @include h5-mixin;
        }
    }
    &__rating{
        margin-bottom: 22px;
        display: flex;
        align-items: center;
        gap: 2px;
    }
    &__review{
        @include text-medium-mixin;
    }
}

@media (max-width: 1360px) {
    .review-card{
        padding: 30px;
        width: 360px;
        height: 360px;
    }
}

@media (max-width: 920px) {
    .review-card{
        border-radius: 20px;
        padding: 24px;
        width: 320px;
        height: 320px;
    }
}

@media (max-width: 720px) {
    .review-card{
        border-radius: 16px;
        padding: 12px;
        width: 300px;
        height: 300px;
    }
}
</style>
