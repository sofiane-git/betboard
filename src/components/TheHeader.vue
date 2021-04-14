<template>
<div>
    <nav class="h-20 flex flex-row p-3 items-center">
        <div class="">
            <a href="#" class="flex flex-row items-center overflow-hidden">
                <img class="h-12" src="https://lh3.googleusercontent.com/proxy/vsd5izUO9OxkbiJAR1yChihVR_7jVcLuKkhdRy7HAXR5b4qLqUhWC7iu0ibTlx5w16P9MmDDZUe6XujvVgJ5abejYnFnSVRlBapmYRlPGEpeUobuaw-5iuXK" alt="logo">
                <span class="underline-hover px-4 letter-spacing">BET|BOARD</span>
            </a>
        </div>
        <div class="flex flex-row items-center justify-between flex-1">
            <div class="w-5/12">
                <ul class="flex flex-row justify-around w-full">
                    <li><a class="underline-hover" href="#">Stats</a></li>
                    <li><a class="underline-hover" href="#">Bankroll</a></li>
                </ul>
            </div>
            <div>
                <button class="rounded-full h-12 button-profil">
                    <span class="underline-hover-right pl-3">Mon profil</span>
                </button>

            </div>
        </div>
    </nav>
</div>
</template>

<script>

export default {

}
</script>

<style>
.underline-hover::after {
    content: '';
    display: block;
    width: 120%;
    height: 1px;
    background-color: rgba(217, 119, 6, 0.5);
    transition-duration: 0.30s;
    transform-origin: left center;
    transform: scale(0);
}
.underline-hover:hover::after {
    transform: scale(1);
}

.underline-hover-right::after {
    content: '';
    display: block;
    width: 105%;
    height: 1px;
    background-color: rgba(217, 119, 6, 0.5);
    transition-duration: 0.30s;
    transform-origin: right center;
    transform: scale(0);
}
.underline-hover-right:hover::after {
    transform: scale(1);
}

.button-profil:focus {
  outline: none;
}

.letter-spacing {
    letter-spacing: 0.3em
}

</style>
