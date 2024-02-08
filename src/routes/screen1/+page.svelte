<script>
    // import { debounce } from 'lodash';
    import pkg from 'lodash';
    const {debounce} = pkg;

    let searchTerm = '';
    
    const handleSearch = debounce(() => {
        console.log('Searching for:', searchTerm);
        // You can perform your search logic here
    }, 300);

    function handleInputChange(event) {
        searchTerm = event.target.value;
        handleSearch();
    }

    function handleKeyPress(event) {
        if (event.key === 'Enter') {
            handleSearch();
        }
    }

	/** @type {import('./$types').PageData} */
	export let data;
</script>

<style>
    .search-bar {
        width: 100%;
        padding: 8px;
        font-size: 16px;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-sizing: border-box;
        margin-bottom: 10px;
    }
</style>

<a href="/">Home</a>
<h1>Screen1</h1>
<input 
    type="text" 
    class="search-bar" 
    placeholder="Search..." 
    bind:value={searchTerm} 
    on:input={handleInputChange} 
    on:keypress={handleKeyPress}
/>
<div id="searchResults"></div>