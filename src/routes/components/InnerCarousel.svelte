<!-- InnerCarousel.svelte -->
<script>
    import ProjectCard from "./ProjectCard.svelte";
    export let projects = [];
    export let currentProjectIndex = 0;
    export let onProjectChange;

    let transitioning = false; // Track if a transition is happening

    function prevProject() {
        if (transitioning) return; // Prevent multiple clicks during transition
        transitioning = true;
        const newIndex = (currentProjectIndex - 1 + projects.length) % projects.length;
        onProjectChange(newIndex);
        setTimeout(() => transitioning = false, 300); // Adjust timeout to match animation duration
    }

    function nextProject() {
        if (transitioning) return; // Prevent multiple clicks during transition
        transitioning = true;
        const newIndex = (currentProjectIndex + 1) % projects.length;
        onProjectChange(newIndex);
        setTimeout(() => transitioning = false, 300); // Adjust timeout to match animation duration
    }

    // New function to handle category changes
    export function handleCategoryChange() {
        transitioning = true; // Set transitioning to true
        setTimeout(() => {
            transitioning = false; // Reset after transition time
        }, 300); // Match this duration with the CSS transition duration
    }
</script>

<div class="inner-carousel">
    <button on:click={prevProject}>⟨</button>

    <div class="project-content {transitioning ? 'fade-out' : 'fade-in'}">
        <!-- Display current project -->
        {#if projects.length > 0}
            <ProjectCard
                title={projects[currentProjectIndex].title}
                description={projects[currentProjectIndex].description}
                image={projects[currentProjectIndex].image}
            />
        {/if}
    </div>

    <button on:click={nextProject}>⟩</button>
</div>

<style>
    .inner-carousel {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 1rem;
    }

    .inner-carousel button {
        background: none;
        border: none;
        font-size: 2rem;
        cursor: pointer;
    }

    .project-content {
        position: relative; /* Enable positioning for transitions */
        transition: opacity 0.3s ease, transform 0.3s ease; /* Transition for opacity and transform */
    }

    .fade-in {
        opacity: 1; /* Fully visible */
        transform: translateY(0); /* Normal position */
    }

    .fade-out {
        opacity: 0; /* Fade out */
        transform: translateY(-10px); /* Move up slightly during fade */
    }
</style>
