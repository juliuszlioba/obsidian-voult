<nav x-data="{
    scrollPos: window.pageYOffset,
    isVisible: true,
    handleScroll() {
        const currentScroll = window.pageYOffset;
        this.isVisible = this.scrollPos > currentScroll || currentScroll < 50;
        this.scrollPos = currentScroll;
    }
}" 
    @scroll.window="handleScroll()"
    :class="{ 'translate-y-0': isVisible, '-translate-y-full': !isVisible }"
    class="fixed top-0 left-0 right-0 transition-transform duration-300 bg-white shadow-md z-50"
>
    <!-- Your navigation content here -->
</nav>
<nav x-data="{
    scrollPos: window.pageYOffset,
    isVisible: true,
    handleScroll() {
        const currentScroll = window.pageYOffset;
        this.isVisible = this.scrollPos > currentScroll || currentScroll < 50;
        this.scrollPos = currentScroll;
    }
}" 
    @scroll.window="handleScroll()"
    :class="{ 'translate-y-0': isVisible, '-translate-y-full': !isVisible }"
    class="fixed top-0 left-0 right-0 transition-transform duration-300 bg-white shadow-md z-50"
>
    <!-- Your navigation content here -->
</nav>
<nav x-data="{
    scrollPos: window.pageYOffset,
    isVisible: true,
    handleScroll() {
        const currentScroll = window.pageYOffset;
        this.isVisible = this.scrollPos > currentScroll || currentScroll < 50;
        this.scrollPos = currentScroll;
    }
}" 
    @scroll.window="handleScroll()"
    :class="{ 'translate-y-0': isVisible, '-translate-y-full': !isVisible }"
    class="fixed top-0 left-0 right-0 transition-transform duration-300 bg-white shadow-md z-50"
>
    <!-- Your navigation content here -->
</nav>
### Simple version:

```html
<nav x-data="{
    scrollPos: window.pageYOffset,
    isVisible: true,
    handleScroll() {
        const currentScroll = window.pageYOffset;
        this.isVisible = this.scrollPos > currentScroll || currentScroll < 50;
        this.scrollPos = currentScroll;
    }
}" 
    @scroll.window="handleScroll()"
    :class="{ 'translate-y-0': isVisible, '-translate-y-full': !isVisible }"
    class="fixed top-0 left-0 right-0 transition-transform duration-300 bg-white shadow-md z-50"
>
    <!-- Your navigation content here -->
</nav>
```

### Advanced version:

```html
<nav x-data="{
    scrollPos: window.pageYOffset,
    isVisible: true,
    timeout: null,
    handleScroll() {
        if (this.timeout) {
            window.cancelAnimationFrame(this.timeout);
        }
        
        this.timeout = window.requestAnimationFrame(() => {
            const currentScroll = window.pageYOffset;
            this.isVisible = this.scrollPos > currentScroll || currentScroll < 50;
            this.scrollPos = currentScroll;
        });
    }
}" 
    @scroll.window="handleScroll()"
    :class="{ 
        'translate-y-0': isVisible, 
        '-translate-y-full': !isVisible 
    }"
    class="fixed top-0 left-0 right-0 transition-transform duration-300 bg-white shadow-md z-50"
>
    <!-- Your navigation content here -->
</nav>
```