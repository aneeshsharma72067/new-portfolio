<template>
    <section id="testimonials" class="my-4">
        <h1 class="text-6xl font-bold my-5 leading-snug text-center sm:leading-none">
            Testimonials
        </h1>
        <p class="text-center text-gray-500 text-lg">
            See what my clients say about me !
        </p>
        <div class="flex items-center justify-center my-10 w-full">
            <Testimonial />
        </div>
    </section>
</template>

<script>
import Testimonial from './Testimonial.vue';

export default {
    name: "TestimonialsComponent",
    components: { Testimonial }
}
</script>
