<template>
    <div class="main-comp">
        <div class="flex flex-col md:flex-row mx-4 md:mx-0 card max-w-5xl w-full">
            <!-- Left side - Logo and Info -->
            <div class="logo-container text-gray-800 p-10 md:w-2/5 flex flex-col justify-center items-center py-12">
                <div class="logo mb-6">
                    <!-- Custom RPS Logo -->
                    <div class="rps-logo bg-gradient-to-br from-blue-100 to-indigo-100 p-6 rounded-2xl shadow-inner">
                        <svg xmlns="http://www.w3.org/2000/svg" width="90" height="90" viewBox="0 0 100 100">
                            <defs>
                                <linearGradient id="gradient" x1="0%" y1="0%" x2="100%" y2="100%">
                                    <stop offset="0%" stop-color="#8b5cf6" />
                                    <stop offset="100%" stop-color="#3b82f6" />
                                </linearGradient>
                            </defs>
                            <circle cx="50" cy="50" r="45" fill="url(#gradient)" />
                            <!-- RPS Icon - simplified design -->
                            <rect x="25" y="30" width="50" height="8" rx="4" fill="white" />
                            <rect x="25" y="42" width="35" height="6" rx="3" fill="white" />
                            <rect x="25" y="52" width="25" height="6" rx="3" fill="white" />
                            <circle cx="70" cy="65" r="8" fill="white" />
                        </svg>
                    </div>
                </div>

                <h1
                    class="text-4xl font-bold mb-2 tracking-tight bg-gradient-to-r from-purple-600 to-blue-600 bg-clip-text text-transparent">
                    RPS
                </h1>
                <p class="text-center text-gray-600 text-lg mb-8 font-medium">Result Processing System</p>

                <div class="space-y-3 mt-6 w-full max-w-xs">
                    <div class="feature-point bg-blue-50 p-3 rounded-lg text-sm font-medium">✓ Automated grade
                        calculations</div>
                    <div class="feature-point bg-blue-50 p-3 rounded-lg text-sm font-medium">✓ Secure result storage
                    </div>
                    <div class="feature-point bg-blue-50 p-3 rounded-lg text-sm font-medium">✓ Transparent management
                    </div>
                    <div class="feature-point bg-blue-50 p-3 rounded-lg text-sm font-medium">✓ Instant mark sheet
                        generation</div>
                </div>

                <div class="mt-10 pt-6 border-t border-gray-200 w-full max-w-xs text-center">
                    <p class="text-sm text-gray-500 font-medium">Trusted by educational institutions worldwide</p>
                </div>
            </div>

            <!-- Right side - Login Form -->
            <div class="bg-white p-10 md:w-3/5 py-12">
                <h2 class="text-3xl font-bold text-gray-800 mb-2">Secure Access Portal</h2>
                <p class="text-gray-600 mb-8 font-medium">Sign in to manage academic results</p>

                <form class="space-y-6" @submit.prevent="handleLogin">
                    <div>
                        <label for="email" class="block text-gray-700 font-semibold mb-2">Institutional Email</label>
                        <div class="relative">
                            <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                <svg class="w-5 h-5 text-gray-400" fill="none" stroke="currentColor"
                                    viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z">
                                    </path>
                                </svg>
                            </div>
                            <input type="email" id="email" v-model="email"
                                class="input-field pl-10 w-full px-4 py-4 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                                placeholder="faculty@institution.edu">
                        </div>
                    </div>

                    <div>
                        <label for="password" class="block text-gray-700 font-semibold mb-2">Password</label>
                        <div class="relative">
                            <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                <svg class="w-5 h-5 text-gray-400" fill="none" stroke="currentColor"
                                    viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z">
                                    </path>
                                </svg>
                            </div>
                            <input :type="showPassword ? 'text' : 'password'" id="password" v-model="password"
                                class="input-field pl-10 pr-12 w-full px-4 py-4 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                                placeholder="••••••••">
                            <button type="button" @click="togglePasswordVisibility"
                                class="password-toggle absolute inset-y-0 right-0 flex items-center justify-center w-12 text-gray-400 hover:text-gray-600 transition-colors focus:outline-none">
                                <svg v-if="showPassword" class="w-5 h-5" fill="none" stroke="currentColor"
                                    viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M13.875 18.825A10.05 10.05 0 0112 19c-4.478 0-8.268-2.943-9.543-7a9.97 9.97 0 011.563-3.029m5.858.908a3 3 0 114.243 4.243M9.878 9.878l4.242 4.242M9.878 9.878L3 3m6.878 6.878L21 21">
                                    </path>
                                </svg>
                                <svg v-else class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path>
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z">
                                    </path>
                                </svg>
                            </button>
                        </div>
                    </div>

                    <div class="flex justify-between items-center">
                        <div class="flex items-center">
                            <input type="checkbox" id="remember" v-model="rememberMe"
                                class="h-4 w-4 text-purple-600 focus:ring-purple-500 border-gray-300 rounded">
                            <label for="remember" class="ml-2 block text-sm text-gray-700 font-medium">Remember this
                                device</label>
                        </div>

                        <a href="#"
                            class="text-sm text-purple-600 hover:text-purple-800 transition-colors font-medium">Forgot
                            password?</a>
                    </div>

                    <button type="submit"
                        class="btn-primary w-full text-white py-4 px-4 rounded-lg font-semibold transition-all duration-300 hover:shadow-lg">
                        Access Dashboard
                    </button>
                </form>

                <div class="divider my-8">Secure & Encrypted</div>

                <div class="text-center">
                    <p class="text-sm text-gray-600 font-medium">
                        Need access?
                        <a href="#" class="text-purple-600 hover:text-purple-800 font-semibold transition-colors">
                            Contact system administrator
                        </a>
                    </p>
                </div>

                <div class="mt-10 border-t border-gray-100 pt-6">
                    <p class="text-xs text-gray-500 text-center font-medium">© 2023 RPS - Result Processing System. All
                        rights
                        reserved.</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'LoginPage',
    data() {
        return {
            email: '',
            password: '',
            rememberMe: false,
            showPassword: false
        }
    },
    methods: {
        handleLogin() {
            console.log('Login attempted', { email: this.email, rememberMe: this.rememberMe });
        },
        togglePasswordVisibility() {
            this.showPassword = !this.showPassword;
        }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

.main-comp {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', sans-serif;
    background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: 500;
    letter-spacing: -0.025em;
}

.card {
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.1), 0 10px 30px -10px rgba(0, 0, 0, 0.05);
    border-radius: 1.5rem;
    overflow: hidden;
    background: white;
}

.logo-container {
    background: linear-gradient(135deg, #f8fafc 0%, #e0f2fe 100%);
    position: relative;
    overflow: hidden;
    border-right: 1px solid #e2e8f0;
}

.input-field {
    transition: all 0.3s ease;
    font-family: inherit;
    font-weight: 500;
    font-size: 15px;
}

.password-toggle {
    background: none;
    border: none;
    cursor: pointer;
    border-radius: 0 0.5rem 0.5rem 0;
}

.password-toggle:hover {
    background-color: rgba(139, 92, 246, 0.05);
}

.password-toggle:focus {
    background-color: rgba(139, 92, 246, 0.1);
}

.btn-primary {
    background: linear-gradient(135deg, #8b5cf6 0%, #3b82f6 100%);
    border: none;
    position: relative;
    overflow: hidden;
    font-family: inherit;
    font-weight: 600;
    font-size: 16px;
}

.btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 25px -5px rgba(139, 92, 246, 0.4);
}

.feature-point {
    color: #475569;
    display: flex;
    align-items: center;
    font-weight: 500;
}

.divider {
    display: flex;
    align-items: center;
    text-align: center;
    color: #64748b;
    font-size: 0.875rem;
    font-weight: 500;
}

.divider::before,
.divider::after {
    content: '';
    flex: 1;
    border-bottom: 1px solid #e2e8f0;
}

.divider::before {
    margin-right: 0.5em;
}

.divider::after {
    margin-left: 0.5em;
}

.rps-logo {
    filter: drop-shadow(0 4px 3px rgb(0 0 0 / 0.07));
}

h1,
h2 {
    font-weight: 800;
    letter-spacing: -0.05em;
}

p {
    font-weight: 500;
}

label {
    font-weight: 600;
}
</style>