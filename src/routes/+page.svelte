<!-- src/routes/index.svelte -->
<script>
    // Your script here
    import OuterCarousel from "./components/OuterCarousel.svelte";
    import InnerCarousel from "./components/InnerCarousel.svelte";
  
    let projectCategories = [
        {
            category: "Website Design",
            projects: [
                { title: "Website 1", description: "A modern, responsive website.", image: "/images/Screenshot_(5).png" },
            ]
        },
        {
            category: "Illustration",
            projects: [
                { title: "Illustration 1", description: "Hand-drawn illustration.", image: "/images/Pickle_Springs.png" },
            ]
        },
        {
            category: "Programming",
            projects: [
                { title: "Along The Way", description: "Interactive coding project.", image: "/images/logo-with-text.png" },
            ]
        }
    ];
  
    let currentCategoryIndex = 0;
    let currentProjectIndex = 0;
  
    function handleCategoryChange(newIndex) {
        currentCategoryIndex = newIndex;
        currentProjectIndex = 0; // Reset project index when changing category
    }
  
    function handleProjectChange(newIndex) {
        currentProjectIndex = newIndex;
    }
  </script>
  
  <section class="p-8">
    <h2 class="text-center text-3xl font-bold mb-8">My Portfolio</h2>
    <OuterCarousel
        projectCategories={projectCategories}
        currentCategoryIndex={currentCategoryIndex}
        onCategoryChange={handleCategoryChange}
    />
    <InnerCarousel
        projects={projectCategories[currentCategoryIndex].projects}
        currentProjectIndex={currentProjectIndex}
        onProjectChange={handleProjectChange}
    />
  </section>
  
  <style>
    section {
        padding: 2rem;
    }
  </style>
  