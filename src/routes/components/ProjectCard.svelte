<script>
    export let title = "Default Project Title";
    export let description = "Default Project Description";
    export let image = "";  // Default value for image
</script>

<div class="card bg-white shadow-lg rounded-lg overflow-hidden">
    <img src={image} alt={title} class="w-full h-48 object-cover" />
    <div class="p-4 text-center">
        <h3 class="text-xl font-bold">{title}</h3>
        <p class="text-gray-600 mt-2">{description}</p>
        <button class="mt-4 px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600">
            Learn More
        </button>
    </div>
</div>

<style>
    .card {
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Subtle shadow for the lift effect */
    }

    .card:hover {
        transform: scale(1.05);
        box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); /* Slightly stronger shadow on hover */
    }

    img {
        max-height: 200px;
        object-fit: cover;
    }

    h3 {
        font-size: 1.5rem;
        margin-bottom: 0.5rem;
    }

    button {
        transition: background-color 0.3s ease;
    }
</style>
