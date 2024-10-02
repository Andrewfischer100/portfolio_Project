<!-- OuterCarousel.svelte -->
<script>
    export let projectCategories = [];
    export let currentCategoryIndex = 0;
    export let onCategoryChange;

    let transitioning = false; // Track if a transition is happening

    function prevCategory() {
        if (transitioning) return; // Prevent multiple clicks during transition
        transitioning = true;
        const newIndex = (currentCategoryIndex - 1 + projectCategories.length) % projectCategories.length;
        onCategoryChange(newIndex);
        setTimeout(() => transitioning = false, 300); // Adjust timeout to match animation duration
    }

    function nextCategory() {
        if (transitioning) return; // Prevent multiple clicks during transition
        transitioning = true;
        const newIndex = (currentCategoryIndex + 1) % projectCategories.length;
        onCategoryChange(newIndex);
        setTimeout(() => transitioning = false, 300); // Adjust timeout to match animation duration
    }
</script>

<div class="outer-carousel-nav">
    <button class="nav-button prev" on:click={prevCategory}>⟨</button>

    <div class="category-content {transitioning ? 'fade-out' : 'fade-in'}">
        <h2>{projectCategories[currentCategoryIndex].category}</h2>
        <slot />  <!-- Inner carousel is displayed here -->
    </div>

    <button class="nav-button next" on:click={nextCategory}>⟩</button>
</div>

<style>
    .outer-carousel-nav {
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 2rem;
        gap: 2rem;
        padding: 2rem;
        background-color: #f9f9f9; /* Optional background color */
    }

    .category-content {
        flex-grow: 1;
        text-align: center;
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

    h2 {
        font-size: 2.5rem;  /* Larger font for higher hierarchy */
        font-weight: 700;   /* Make the title bold */
        margin-bottom: 1rem;
        color: #333;  /* Darker color for emphasis */
    }

    .nav-button {
        background: none;
        border: none;
        font-size: 1.5rem; /* Smaller button size for a subtle look */
        color: #666;       /* Softer button color */
        cursor: pointer;
        padding: 0.5rem 1rem;
        transition: color 0.3s ease;
    }

    .nav-button:hover {
        color: #333; /* Slightly darken button on hover */
    }

    .prev, .next {
        position: relative;
        top: -10px; /* Adjust the vertical positioning to align with title */
    }

    .nav-button:active {
        transform: scale(0.95); /* Slightly shrink on press */
    }
</style>
