<template>
    <div>
        <h1 class="text-3xl font-bold">Welcome to Security Playground!</h1>
        <p>Security Playground is a place where you can learn about security vulnerabilities and how to protect yourself from them.</p>
        <hr class="my-8">
        <div class="grid grid-cols-3 gap-4">
            <div class="bg-gray-100 p-4 rounded-lg">
                <nuxt-link to="/profile/signin" class="text-blue-500 font-bold">Sign In</nuxt-link>
            </div>
            <div class="bg-gray-100 p-4 rounded-lg">
                <nuxt-link to="/profile/profile" class="text-blue-500 font-bold">Profile</nuxt-link>
            </div>
            <div class="bg-gray-100 p-4 rounded-lg">
                <nuxt-link to="/profile/settings" class="text-blue-500 font-bold">Settings</nuxt-link>
            </div>
        </div>
    </div>
</template>