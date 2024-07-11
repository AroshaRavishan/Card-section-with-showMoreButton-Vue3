<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue';
import PrimaryButton from "@/Components/Web/WebRevamp/WebCommoncomponents/PrimaryButton.vue";
import SecondaryButton from "@/Components/Web/WebRevamp/WebCommoncomponents/SecondaryButton.vue";

const cards = ref([
    { id: 1, title: 'card1', subtitle:'card1 subtitle' },
    { id: 2, title: 'card2', subtitle:'card2 subtitle'  },
    { id: 3, title: 'card3', subtitle:'card3 subtitle'  },
    { id: 4, title: 'card4', subtitle:'card4 subtitle'  },
    { id: 5, title: 'card5', subtitle:'card5 subtitle'  },
    { id: 6, title: 'card6', subtitle:'card6 subtitle'  },
    { id: 7, title: 'card7', subtitle:'card7 subtitle'  },
    { id: 8, title: 'card8', subtitle:'card8 subtitle'  },
]);

const initialCardCount = ref(6);
const expanded = ref(false);
const sectionRef = ref(null);

const updateInitialCardCount = () => {
    initialCardCount.value = window.innerWidth <= 991 ? 2 : 6;
};

onMounted(() => {
    updateInitialCardCount();
    window.addEventListener('resize', updateInitialCardCount);
});

onUnmounted(() => {
    window.removeEventListener('resize', updateInitialCardCount);
});

const visibleCards = computed(() => {
    return expanded.value ? cards.value : cards.value.slice(0, initialCardCount.value);
});

const showMoreButton = computed(() => {
    return cards.value.length > initialCardCount.value;
});

function toggleExpand() {
    expanded.value = !expanded.value;
    if (!expanded.value) {
        // Scroll to the top of the section when collapsing
        scrollToSection();
    }
}

function scrollToSection() {
    if (sectionRef.value) {
        const offset = 100; // Adjust this value to set your desired top margin
        const elementPosition = sectionRef.value.getBoundingClientRect().top;
        const offsetPosition = elementPosition + window.pageYOffset - offset;
        
        window.scrollTo({
            top: offsetPosition,
            behavior: "smooth"
        });
    }
}
</script>

<template>
    <section ref="sectionRef">
        <div class="container">
            <div class="">
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-3 gap-6 py-10">
                    <transition-group name="card-list">
                        <div v-for="card in visibleCards" :key="card.id" class="flex justify-center">
                            <div class="bg-white rounded-4 shadow-gel-shadow w-full p-4">
                                <div class="">
                                    {{ card.title }}
                                </div>
                                <div class="">
                                    {{ card.subtitle }}
                                </div>
                            </div>
                        </div>
                    </transition-group>
                </div>
                <div class="mt-12 flex justify-center items-center gap-4">
                    <PrimaryButton v-if="showMoreButton" @click="toggleExpand" class="whitespace-nowrap gap-3 flex items-center text-white font-bold py-2.5 px-4 border border-black-800 bg-black-800 rounded-2 text-lg">
                        {{ expanded ? 'Show less' : 'Show more' }}
                    </PrimaryButton>
                    <SecondaryButton>
                        View all
                    </SecondaryButton>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.card-list-enter-active,
.card-list-leave-active {
    transition: opacity 0.5s ease, transform 0.5s ease;
}
.card-list-enter-from,
.card-list-leave-to {
    opacity: 0;
    transform: translateY(30px);
}
</style>