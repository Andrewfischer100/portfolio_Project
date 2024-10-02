<script>
    import ProjectCard from './ProjectCard.svelte';

    let projects = [
        { title: "Website Design", description: "A modern, responsive website.", image: "/images/Screenshot_(5).png" },
        { title: "Illustration", description: "Detailed hand-drawn illustrations.", image: "/images/Pickle_Springs.png" },
        { title: "Programming", description: "Interactive and dynamic coding projects.", image: "/images/logo-with-text.png" },
        { title: "Poster Design", description: "Express yourself!", image: "/images/70aa4e69-f223-4941-8324-fe47c08a80e3_rw_1200.png" },
        { title: "Branding & Mockups", description: "Conceptual Design for Brand Identity", image: "/images/ed1aa1122009429.60d140c339aff.png" }
        ];
</script>

<section class="p-8">
    <h2 class="text-center text-3xl font-bold mb-8">My Portfolio</h2>
    <div class="grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
        {#each projects as project}
            <ProjectCard title={project.title} description={project.description} image={project.image} />
        {/each}
    </div>
</section>


<style>
    section {
        padding: 2rem;
    }
</style>
