<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Privacy Checkup & Awareness Test</title>
    <meta name="description" content="Test your privacy awareness and find out your online security score.">

    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link
        href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;800&family=Inter:wght@400;500;700&display=swap"
        rel="stylesheet">

    <!-- Custom CSS -->
    <link rel="stylesheet" href="styles.css">
<style>
:root {
    --bg-color: #0f111a;
    --card-bg: rgba(26, 30, 43, 0.6);
    --card-border: rgba(255, 255, 255, 0.08);
    --text-primary: #ffffff;
    --text-secondary: #a0a8c0;

    --primary-color: #6366f1;
    --primary-hover: #4f46e5;
    --secondary-color: #10b981;
    --danger-color: #ef4444;
    --warning-color: #f59e0b;

    --gradient-1: linear-gradient(135deg, #6366f1 0%, #a855f7 100%);
    --gradient-2: linear-gradient(135deg, #3b82f6 0%, #2dd4bf 100%);

    --font-heading: 'Outfit', sans-serif;
    --font-body: 'Inter', sans-serif;

    --shadow-sm: 0 4px 6px rgba(0, 0, 0, 0.1);
    --shadow-md: 0 10px 15px -3px rgba(0, 0, 0, 0.2);
    --shadow-lg: 0 20px 25px -5px rgba(0, 0, 0, 0.3);
    --shadow-glow: 0 0 20px rgba(99, 102, 241, 0.3);

    --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background-color: var(--bg-color);
    color: var(--text-primary);
    font-family: var(--font-body);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-x: hidden;
    position: relative;
    line-height: 1.6;
}

/* Background animated blobs */
.background-animation {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    z-index: -1;
    overflow: hidden;
}

.blob {
    position: absolute;
    filter: blur(80px);
    opacity: 0.6;
    animation: float 10s infinite alternate ease-in-out;
    border-radius: 50%;
}

.blob-1 {
    top: -10%;
    left: -10%;
    width: 50vw;
    height: 50vw;
    background: rgba(99, 102, 241, 0.4);
    animation-delay: 0s;
}

.blob-2 {
    bottom: -20%;
    right: -10%;
    width: 60vw;
    height: 60vw;
    background: rgba(168, 85, 247, 0.3);
    animation-delay: -5s;
}

.blob-3 {
    top: 40%;
    left: 60%;
    width: 40vw;
    height: 40vw;
    background: rgba(45, 212, 191, 0.2);
    animation-delay: -2s;
}

@keyframes float {
    0% {
        transform: translate(0, 0) scale(1);
    }

    100% {
        transform: translate(30px, 50px) scale(1.1);
    }
}

/* Glassmorphism Container */
.container {
    width: 100%;
    max-width: 650px;
    padding: 2rem;
    position: relative;
    z-index: 10;
}

.screen {
    display: none;
    background: var(--card-bg);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    border: 1px solid var(--card-border);
    border-radius: 24px;
    padding: 3rem 2.5rem;
    box-shadow: var(--shadow-lg);
    animation: fadeIn 0.5s ease forwards;
    transform: translateY(20px);
    opacity: 0;
}

.screen.active {
    display: flex;
    flex-direction: column;
    animation: slideUp 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

@keyframes slideUp {
    to {
        transform: translateY(0);
        opacity: 1;
    }
}

@keyframes fadeIn {
    to {
        opacity: 1;
    }
}

/* Typography */
h1,
h2,
h3 {
    font-family: var(--font-heading);
    letter-spacing: -0.02em;
}

header {
    text-align: center;
    margin-bottom: 2.5rem;
}

h1 {
    font-size: 2.5rem;
    font-weight: 800;
    margin-bottom: 0.5rem;
    background: var(--gradient-1);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

.gradient-text {
    background: var(--gradient-2);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

p {
    color: var(--text-secondary);
    font-size: 1.1rem;
}

/* Start Screen Specific */
.icon-wrapper {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background: rgba(99, 102, 241, 0.1);
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 auto 1.5rem;
    color: var(--primary-color);
    box-shadow: var(--shadow-glow);
}

.intro-text {
    text-align: center;
    margin-bottom: 2.5rem;
    line-height: 1.8;
}

/* Buttons */
button {
    font-family: var(--font-heading);
    cursor: pointer;
    border: none;
    outline: none;
    font-weight: 600;
    font-size: 1.1rem;
    border-radius: 12px;
    padding: 1rem 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
    transition: var(--transition);
    width: 100%;
}

.primary-btn {
    background: var(--gradient-1);
    color: white;
    box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
}

.primary-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(99, 102, 241, 0.6);
}

.primary-btn:active {
    transform: translateY(1px);
}

.secondary-btn {
    background: rgba(255, 255, 255, 0.05);
    color: white;
    border: 1px solid rgba(255, 255, 255, 0.1);
}

.secondary-btn:hover:not(:disabled) {
    background: rgba(255, 255, 255, 0.1);
}

.secondary-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}

.mt-4 {
    margin-top: 2rem;
}

/* Pulse animation for start button */
@keyframes pulse {
    0% {
        box-shadow: 0 0 0 0 rgba(99, 102, 241, 0.4);
    }

    70% {
        box-shadow: 0 0 0 15px rgba(99, 102, 241, 0);
    }

    100% {
        box-shadow: 0 0 0 0 rgba(99, 102, 241, 0);
    }
}

.pulse {
    animation: pulse 2s infinite;
}

/* Quiz Screen Specific */
.quiz-header {
    margin-bottom: 2rem;
}

.progress-container {
    width: 100%;
    height: 6px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 3px;
    margin-bottom: 1rem;
    overflow: hidden;
}

.progress-bar {
    height: 100%;
    background: var(--gradient-2);
    width: 5%;
    border-radius: 3px;
    transition: width 0.4s ease;
}

.quiz-meta {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 0.9rem;
    color: var(--text-secondary);
    font-weight: 500;
}

.category-badge {
    background: rgba(99, 102, 241, 0.15);
    color: #818cf8;
    padding: 0.3rem 0.8rem;
    border-radius: 20px;
    border: 1px solid rgba(99, 102, 241, 0.2);
}

.question-text {
    font-size: 1.5rem;
    margin-bottom: 2rem;
    line-height: 1.4;
    color: white;
}

.options-container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    margin-bottom: 2rem;
}

.option-btn {
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid var(--card-border);
    color: white;
    padding: 1.2rem;
    border-radius: 12px;
    font-size: 1rem;
    text-align: left;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    transition: var(--transition);
    position: relative;
    overflow: hidden;
}

.option-btn:hover {
    background: rgba(255, 255, 255, 0.08);
    transform: translateX(4px);
    border-color: rgba(255, 255, 255, 0.2);
}

.option-btn.selected {
    background: rgba(99, 102, 241, 0.15);
    border-color: var(--primary-color);
    box-shadow: 0 0 15px rgba(99, 102, 241, 0.2);
}

.option-btn.selected::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 4px;
    background: var(--primary-color);
}

/* Results Screen Specific */
.score-display {
    width: 160px;
    margin: 0 auto 1.5rem;
}

.circular-chart {
    display: block;
    margin: 0 auto;
    max-width: 80%;
    max-height: 250px;
}

.circle-bg {
    fill: none;
    stroke: rgba(255, 255, 255, 0.05);
    stroke-width: 2.5;
}

.circle {
    fill: none;
    stroke-width: 2.5;
    stroke-linecap: round;
    transition: stroke-dasharray 1.5s ease-out, stroke 0.5s ease;
}

.percentage {
    fill: white;
    font-family: var(--font-heading);
    font-weight: 800;
    font-size: 10px;
    text-anchor: middle;
}

.score-title {
    font-size: 2rem;
    margin-bottom: 0.5rem;
}

.score-desc {
    margin-bottom: 2rem;
}

.feedback-secton {
    text-align: left;
    background: rgba(0, 0, 0, 0.2);
    border-radius: 16px;
    padding: 1.5rem;
    border: 1px solid var(--card-border);
}

.feedback-secton h3 {
    margin-bottom: 1rem;
    color: white;
    font-size: 1.2rem;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    padding-bottom: 0.5rem;
}

.feedback-list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.feedback-item {
    font-size: 0.95rem;
    color: var(--text-secondary);
    display: flex;
    gap: 0.8rem;
    align-items: flex-start;
}

.feedback-item::before {
    content: '→';
    color: var(--primary-color);
    font-weight: bold;
}

.feedback-item.good::before {
    content: '✓';
    color: var(--secondary-color);
}

.feedback-item.bad::before {
    content: '!';
    color: var(--danger-color);
}

/* Responsive adjustments */
@media (max-width: 600px) {
    .container {
        padding: 1rem;
    }

    .screen {
        padding: 2rem 1.5rem;
    }

    h1 {
        font-size: 2rem;
    }

    .question-text {
        font-size: 1.25rem;
    }
}

</style>
</head>

<body>
    <div class="background-animation">
        <div class="blob blob-1"></div>
        <div class="blob blob-2"></div>
        <div class="blob blob-3"></div>
    </div>

    <main class="container">
        <!-- Start Screen -->
        <section id="start-screen" class="screen active">
            <header>
                <div class="icon-wrapper">
                    <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none"
                        stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                        class="shield-icon">
                        <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
                    </svg>
                </div>
                <h1>Privacy Checkup</h1>
                <p>Test your online safety and security awareness.</p>
            </header>
            <div class="content">
                <p class="intro-text">Answer 20 quick questions to find out your privacy risk score and get personalized
                    recommendations on what to improve.</p>
                <button id="start-btn" class="primary-btn pulse">Start Checkup <span class="arrow">→</span></button>
            </div>
        </section>

        <!-- Quiz Screen -->
        <section id="quiz-screen" class="screen">
            <header class="quiz-header">
                <div class="progress-container">
                    <div class="progress-bar" id="progress-bar"></div>
                </div>
                <div class="quiz-meta">
                    <span id="question-category" class="category-badge">Category</span>
                    <span id="question-count">Question 1 / 20</span>
                </div>
            </header>
            <div class="content quiz-content">
                <h2 id="question-text" class="question-text">Question goes here?</h2>
                <div id="options-container" class="options-container">
                    <!-- Options will be injected by JS -->
                </div>
            </div>
            <div class="quiz-footer">
                <button id="next-btn" class="secondary-btn" disabled>Next Question</button>
            </div>
        </section>

        <!-- Result Screen -->
        <section id="result-screen" class="screen">
            <header>
                <h1 class="gradient-text">Your Privacy Score</h1>
                <div class="score-display">
                    <svg class="circular-chart" viewBox="0 0 36 36">
                        <path class="circle-bg" d="M18 2.0845
                            a 15.9155 15.9155 0 0 1 0 31.831
                            a 15.9155 15.9155 0 0 1 0 -31.831" />
                        <path class="circle" id="score-circle" stroke-dasharray="0, 100" d="M18 2.0845
                            a 15.9155 15.9155 0 0 1 0 31.831
                            a 15.9155 15.9155 0 0 1 0 -31.831" />
                        <text x="18" y="20.35" class="percentage" id="score-text">0</text>
                    </svg>
                </div>
                <h2 id="score-title" class="score-title">Calculating...</h2>
                <p id="score-desc" class="score-desc">Please wait.</p>
            </header>
            <div class="content results-content">
                <div class="feedback-secton">
                    <h3>Areas to Improve</h3>
                    <div id="feedback-list" class="feedback-list">
                        <!-- Dynamic feedback -->
                    </div>
                </div>
                <button id="restart-btn" class="primary-btn mt-4">Retake Checkup</button>
            </div>
        </section>
    </main>

    <!-- Custom JS -->
    <script >
// Quiz Data based on user requirements
const quizData = [
    // Basic Privacy Awareness
    {
        id: 1,
        category: "Basic Privacy Awareness",
        question: "Do you use the same password for multiple apps or websites?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 2,
        category: "Basic Privacy Awareness",
        question: "Is two-factor authentication (OTP or authenticator app) enabled on your main accounts?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 3,
        category: "Basic Privacy Awareness",
        question: "Do you check app permissions (camera, mic, location) before installing apps?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 4,
        category: "Basic Privacy Awareness",
        question: "Have you ever clicked on a suspicious link sent on WhatsApp, email, or SMS?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 5,
        category: "Basic Privacy Awareness",
        question: "Do you regularly update your phone and apps?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },

    // Social Media Privacy
    {
        id: 6,
        category: "Social Media Privacy",
        question: "Is your social media account public or private?",
        options: [
            { text: "Public", score: 0 },
            { text: "Private", score: 1 }
        ]
    },
    {
        id: 7,
        category: "Social Media Privacy",
        question: "Do you accept follow requests from people you don’t know?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 8,
        category: "Social Media Privacy",
        question: "Have you ever shared your live location publicly on social media?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 9,
        category: "Social Media Privacy",
        question: "Do you review tagged photos/posts before they appear on your profile?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 10,
        category: "Social Media Privacy",
        question: "Do you know how to change privacy settings on your social media accounts?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },

    // Data & Security
    {
        id: 11,
        category: "Data & Security",
        question: "Do you use public Wi-Fi for banking or payments?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 12,
        category: "Data & Security",
        question: "Have you ever saved your card details on random websites?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 13,
        category: "Data & Security",
        question: "Do you log out from accounts when using someone else’s device?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 14,
        category: "Data & Security",
        question: "Do you back up your important data (photos, documents)?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 15,
        category: "Data & Security",
        question: "Have you ever checked if your email/password was part of a data breach?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },

    // Real Awareness Test
    {
        id: 16,
        category: "Real Awareness Test",
        question: "If you get a call asking for OTP from your bank, what will you do?",
        options: [
            { text: "Share it, as it's from the bank", score: 0 },
            { text: "Disconnect immediately and do not share", score: 1 },
            { text: "Ask them why they need it", score: 0 }
        ]
    },
    {
        id: 17,
        category: "Real Awareness Test",
        question: "What is phishing?",
        options: [
            { text: "A computer virus that deletes files", score: 0 },
            { text: "Fake emails/messages tricking you to steal info", score: 1 },
            { text: "A safe way to transfer files over network", score: 0 }
        ]
    },
    {
        id: 18,
        category: "Real Awareness Test",
        question: "Which is safer: fingerprint lock, PIN, or pattern? Why?",
        options: [
            { text: "Pattern, as it can be complex", score: 0 },
            { text: "PIN, because numbers are secure", score: 0 },
            { text: "Fingerprint/Biometric, as it's unique to you", score: 1 }
        ]
    },
    {
        id: 19,
        category: "Real Awareness Test",
        question: "What would you do if your Instagram account gets hacked?",
        options: [
            { text: "Create a new account immediately", score: 0 },
            { text: "Report to Instagram & use account recovery procedures", score: 1 },
            { text: "Wait to see if the hacker gives it back", score: 0 }
        ]
    },
    {
        id: 20,
        category: "Real Awareness Test",
        question: "Name one thing you should never share online.",
        options: [
            { text: "Your favorite food", score: 0 },
            { text: "OTP, Passwords, or exact address", score: 1 },
            { text: "Vacation photos after the trip", score: 0 }
        ]
    }
];

// State Variables
let currentQuestionIndex = 0;
let userAnswers = []; // Store chosen options

// DOM Elements
const startScreen = document.getElementById('start-screen');
const quizScreen = document.getElementById('quiz-screen');
const resultScreen = document.getElementById('result-screen');

const startBtn = document.getElementById('start-btn');
const nextBtn = document.getElementById('next-btn');
const restartBtn = document.getElementById('restart-btn');

const questionCategory = document.getElementById('question-category');
const questionCount = document.getElementById('question-count');
const progressBar = document.getElementById('progress-bar');
const questionText = document.getElementById('question-text');
const optionsContainer = document.getElementById('options-container');

const scoreCircle = document.getElementById('score-circle');
const scoreText = document.getElementById('score-text');
const scoreTitle = document.getElementById('score-title');
const scoreDesc = document.getElementById('score-desc');
const feedbackList = document.getElementById('feedback-list');

// Event Listeners
startBtn.addEventListener('click', startQuiz);
nextBtn.addEventListener('click', () => {
    if (currentQuestionIndex < quizData.length - 1) {
        currentQuestionIndex++;
        loadQuestion();
    } else {
        showResults();
    }
});
restartBtn.addEventListener('click', resetQuiz);

function switchScreen(screenElement) {
    document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
    screenElement.classList.add('active');
}

function startQuiz() {
    currentQuestionIndex = 0;
    userAnswers = [];
    switchScreen(quizScreen);
    loadQuestion();
}

function loadQuestion() {
    const questionData = quizData[currentQuestionIndex];

    // Update Header Text
    questionCategory.textContent = questionData.category;
    questionCount.textContent = `Question ${currentQuestionIndex + 1} / ${quizData.length}`;

    // Update Progress Bar
    const percent = ((currentQuestionIndex) / quizData.length) * 100;
    progressBar.style.width = `${percent}%`;

    // Set Question
    questionText.textContent = questionData.question;

    // Render Options
    optionsContainer.innerHTML = '';
    questionData.options.forEach((opt, index) => {
        const btn = document.createElement('button');
        btn.classList.add('option-btn');
        btn.textContent = opt.text;

        // Add visual click animation and logic
        btn.addEventListener('click', () => selectOption(btn, opt.score, index));
        optionsContainer.appendChild(btn);
    });

    nextBtn.disabled = true; // Disable Next until answer is selected
}

function selectOption(selectedBtn, scoreValue, optionIndex) {
    // Clear previous selection
    document.querySelectorAll('.option-btn').forEach(btn => btn.classList.remove('selected'));

    // Add selected class
    selectedBtn.classList.add('selected');

    // Save user choice
    userAnswers[currentQuestionIndex] = {
        questionId: quizData[currentQuestionIndex].id,
        category: quizData[currentQuestionIndex].category,
        score: scoreValue
    };

    // Enable Next button
    nextBtn.disabled = false;
}

function calculateCategoryScores() {
    const categoryScores = {
        "Basic Privacy Awareness": { max: 5, actual: 0 },
        "Social Media Privacy": { max: 5, actual: 0 },
        "Data & Security": { max: 5, actual: 0 },
        "Real Awareness Test": { max: 5, actual: 0 }
    };

    userAnswers.forEach(ans => {
        categoryScores[ans.category].actual += ans.score;
    });

    return categoryScores;
}

function showResults() {
    switchScreen(resultScreen);

    const totalScore = userAnswers.reduce((sum, ans) => sum + ans.score, 0);
    const maxScore = quizData.length;

    // Update Chart
    const percentage = Math.round((totalScore / maxScore) * 100);
    scoreText.textContent = `${totalScore}/${maxScore}`;

    // Change circle color based on score
    let circleColor = "var(--danger-color)"; // 0-7
    let title = "High Privacy Risk";
    let desc = "Your online safety practices need immediate attention. You are highly vulnerable to cyber threats.";

    if (totalScore >= 15) {
        circleColor = "var(--secondary-color)";
        title = "Privacy Smart User!";
        desc = "Excellent! You have a very good understanding of online privacy and security.";
    } else if (totalScore >= 8) {
        circleColor = "var(--warning-color)";
        title = "Moderate Awareness";
        desc = "You have okay privacy habits, but there are several areas where you can improve your security.";
    }

    // Delay chart animation slightly
    setTimeout(() => {
        scoreCircle.style.strokeDasharray = `${percentage}, 100`;
        scoreCircle.style.stroke = circleColor;
    }, 100);

    scoreTitle.textContent = title;
    scoreTitle.style.color = circleColor;
    scoreDesc.textContent = desc;

    // Generate Feedback
    generateFeedback(totalScore);
}

function generateFeedback(totalScore) {
    const categoryScores = calculateCategoryScores();
    feedbackList.innerHTML = '';

    const feedbacks = [];

    if (categoryScores["Basic Privacy Awareness"].actual <= 3) {
        feedbacks.push({ type: 'bad', text: "Start using a password manager and enable Two-Factor Authentication (2FA) for major accounts." });
    } else {
        feedbacks.push({ type: 'good', text: "Great job keeping basic password and authentication hygiene." });
    }

    if (categoryScores["Social Media Privacy"].actual <= 3) {
        feedbacks.push({ type: 'bad', text: "Review your social media settings. Consider making your accounts private and stop sharing live locations." });
    }

    if (categoryScores["Data & Security"].actual <= 3) {
        feedbacks.push({ type: 'bad', text: "Avoid public Wi-Fi for banking, and don't save card details on random sites." });
    }

    if (categoryScores["Real Awareness Test"].actual <= 3) {
        feedbacks.push({ type: 'bad', text: "Be highly cautious of phishing links, and never share OTPs over phone calls." });
    }

    if (totalScore === 20) {
        feedbacks.push({ type: 'good', text: "You have a flawless privacy posture! Keep staying updated." });
    }

    feedbacks.forEach(fb => {
        const div = document.createElement('div');
        div.className = `feedback-item ${fb.type}`;
        div.textContent = fb.text;
        feedbackList.appendChild(div);
    });
}

function resetQuiz() {
    progressBar.style.width = '0%';
    scoreCircle.style.strokeDasharray = '0, 100';
    startQuiz();
}

</script>
</body>

</html><!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Privacy Checkup & Awareness Test</title>
    <meta name="description" content="Test your privacy awareness and find out your online security score.">

    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link
        href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;800&family=Inter:wght@400;500;700&display=swap"
        rel="stylesheet">

    <!-- Custom CSS -->
    <link rel="stylesheet" href="styles.css">
<style>
:root {
    --bg-color: #0f111a;
    --card-bg: rgba(26, 30, 43, 0.6);
    --card-border: rgba(255, 255, 255, 0.08);
    --text-primary: #ffffff;
    --text-secondary: #a0a8c0;

    --primary-color: #6366f1;
    --primary-hover: #4f46e5;
    --secondary-color: #10b981;
    --danger-color: #ef4444;
    --warning-color: #f59e0b;

    --gradient-1: linear-gradient(135deg, #6366f1 0%, #a855f7 100%);
    --gradient-2: linear-gradient(135deg, #3b82f6 0%, #2dd4bf 100%);

    --font-heading: 'Outfit', sans-serif;
    --font-body: 'Inter', sans-serif;

    --shadow-sm: 0 4px 6px rgba(0, 0, 0, 0.1);
    --shadow-md: 0 10px 15px -3px rgba(0, 0, 0, 0.2);
    --shadow-lg: 0 20px 25px -5px rgba(0, 0, 0, 0.3);
    --shadow-glow: 0 0 20px rgba(99, 102, 241, 0.3);

    --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background-color: var(--bg-color);
    color: var(--text-primary);
    font-family: var(--font-body);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-x: hidden;
    position: relative;
    line-height: 1.6;
}

/* Background animated blobs */
.background-animation {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    z-index: -1;
    overflow: hidden;
}

.blob {
    position: absolute;
    filter: blur(80px);
    opacity: 0.6;
    animation: float 10s infinite alternate ease-in-out;
    border-radius: 50%;
}

.blob-1 {
    top: -10%;
    left: -10%;
    width: 50vw;
    height: 50vw;
    background: rgba(99, 102, 241, 0.4);
    animation-delay: 0s;
}

.blob-2 {
    bottom: -20%;
    right: -10%;
    width: 60vw;
    height: 60vw;
    background: rgba(168, 85, 247, 0.3);
    animation-delay: -5s;
}

.blob-3 {
    top: 40%;
    left: 60%;
    width: 40vw;
    height: 40vw;
    background: rgba(45, 212, 191, 0.2);
    animation-delay: -2s;
}

@keyframes float {
    0% {
        transform: translate(0, 0) scale(1);
    }

    100% {
        transform: translate(30px, 50px) scale(1.1);
    }
}

/* Glassmorphism Container */
.container {
    width: 100%;
    max-width: 650px;
    padding: 2rem;
    position: relative;
    z-index: 10;
}

.screen {
    display: none;
    background: var(--card-bg);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    border: 1px solid var(--card-border);
    border-radius: 24px;
    padding: 3rem 2.5rem;
    box-shadow: var(--shadow-lg);
    animation: fadeIn 0.5s ease forwards;
    transform: translateY(20px);
    opacity: 0;
}

.screen.active {
    display: flex;
    flex-direction: column;
    animation: slideUp 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

@keyframes slideUp {
    to {
        transform: translateY(0);
        opacity: 1;
    }
}

@keyframes fadeIn {
    to {
        opacity: 1;
    }
}

/* Typography */
h1,
h2,
h3 {
    font-family: var(--font-heading);
    letter-spacing: -0.02em;
}

header {
    text-align: center;
    margin-bottom: 2.5rem;
}

h1 {
    font-size: 2.5rem;
    font-weight: 800;
    margin-bottom: 0.5rem;
    background: var(--gradient-1);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

.gradient-text {
    background: var(--gradient-2);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

p {
    color: var(--text-secondary);
    font-size: 1.1rem;
}

/* Start Screen Specific */
.icon-wrapper {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background: rgba(99, 102, 241, 0.1);
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 auto 1.5rem;
    color: var(--primary-color);
    box-shadow: var(--shadow-glow);
}

.intro-text {
    text-align: center;
    margin-bottom: 2.5rem;
    line-height: 1.8;
}

/* Buttons */
button {
    font-family: var(--font-heading);
    cursor: pointer;
    border: none;
    outline: none;
    font-weight: 600;
    font-size: 1.1rem;
    border-radius: 12px;
    padding: 1rem 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
    transition: var(--transition);
    width: 100%;
}

.primary-btn {
    background: var(--gradient-1);
    color: white;
    box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
}

.primary-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(99, 102, 241, 0.6);
}

.primary-btn:active {
    transform: translateY(1px);
}

.secondary-btn {
    background: rgba(255, 255, 255, 0.05);
    color: white;
    border: 1px solid rgba(255, 255, 255, 0.1);
}

.secondary-btn:hover:not(:disabled) {
    background: rgba(255, 255, 255, 0.1);
}

.secondary-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}

.mt-4 {
    margin-top: 2rem;
}

/* Pulse animation for start button */
@keyframes pulse {
    0% {
        box-shadow: 0 0 0 0 rgba(99, 102, 241, 0.4);
    }

    70% {
        box-shadow: 0 0 0 15px rgba(99, 102, 241, 0);
    }

    100% {
        box-shadow: 0 0 0 0 rgba(99, 102, 241, 0);
    }
}

.pulse {
    animation: pulse 2s infinite;
}

/* Quiz Screen Specific */
.quiz-header {
    margin-bottom: 2rem;
}

.progress-container {
    width: 100%;
    height: 6px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 3px;
    margin-bottom: 1rem;
    overflow: hidden;
}

.progress-bar {
    height: 100%;
    background: var(--gradient-2);
    width: 5%;
    border-radius: 3px;
    transition: width 0.4s ease;
}

.quiz-meta {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 0.9rem;
    color: var(--text-secondary);
    font-weight: 500;
}

.category-badge {
    background: rgba(99, 102, 241, 0.15);
    color: #818cf8;
    padding: 0.3rem 0.8rem;
    border-radius: 20px;
    border: 1px solid rgba(99, 102, 241, 0.2);
}

.question-text {
    font-size: 1.5rem;
    margin-bottom: 2rem;
    line-height: 1.4;
    color: white;
}

.options-container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    margin-bottom: 2rem;
}

.option-btn {
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid var(--card-border);
    color: white;
    padding: 1.2rem;
    border-radius: 12px;
    font-size: 1rem;
    text-align: left;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    transition: var(--transition);
    position: relative;
    overflow: hidden;
}

.option-btn:hover {
    background: rgba(255, 255, 255, 0.08);
    transform: translateX(4px);
    border-color: rgba(255, 255, 255, 0.2);
}

.option-btn.selected {
    background: rgba(99, 102, 241, 0.15);
    border-color: var(--primary-color);
    box-shadow: 0 0 15px rgba(99, 102, 241, 0.2);
}

.option-btn.selected::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 4px;
    background: var(--primary-color);
}

/* Results Screen Specific */
.score-display {
    width: 160px;
    margin: 0 auto 1.5rem;
}

.circular-chart {
    display: block;
    margin: 0 auto;
    max-width: 80%;
    max-height: 250px;
}

.circle-bg {
    fill: none;
    stroke: rgba(255, 255, 255, 0.05);
    stroke-width: 2.5;
}

.circle {
    fill: none;
    stroke-width: 2.5;
    stroke-linecap: round;
    transition: stroke-dasharray 1.5s ease-out, stroke 0.5s ease;
}

.percentage {
    fill: white;
    font-family: var(--font-heading);
    font-weight: 800;
    font-size: 10px;
    text-anchor: middle;
}

.score-title {
    font-size: 2rem;
    margin-bottom: 0.5rem;
}

.score-desc {
    margin-bottom: 2rem;
}

.feedback-secton {
    text-align: left;
    background: rgba(0, 0, 0, 0.2);
    border-radius: 16px;
    padding: 1.5rem;
    border: 1px solid var(--card-border);
}

.feedback-secton h3 {
    margin-bottom: 1rem;
    color: white;
    font-size: 1.2rem;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    padding-bottom: 0.5rem;
}

.feedback-list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.feedback-item {
    font-size: 0.95rem;
    color: var(--text-secondary);
    display: flex;
    gap: 0.8rem;
    align-items: flex-start;
}

.feedback-item::before {
    content: '→';
    color: var(--primary-color);
    font-weight: bold;
}

.feedback-item.good::before {
    content: '✓';
    color: var(--secondary-color);
}

.feedback-item.bad::before {
    content: '!';
    color: var(--danger-color);
}

/* Responsive adjustments */
@media (max-width: 600px) {
    .container {
        padding: 1rem;
    }

    .screen {
        padding: 2rem 1.5rem;
    }

    h1 {
        font-size: 2rem;
    }

    .question-text {
        font-size: 1.25rem;
    }
}

</style>
</head>

<body>
    <div class="background-animation">
        <div class="blob blob-1"></div>
        <div class="blob blob-2"></div>
        <div class="blob blob-3"></div>
    </div>

    <main class="container">
        <!-- Start Screen -->
        <section id="start-screen" class="screen active">
            <header>
                <div class="icon-wrapper">
                    <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none"
                        stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                        class="shield-icon">
                        <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
                    </svg>
                </div>
                <h1>Privacy Checkup</h1>
                <p>Test your online safety and security awareness.</p>
            </header>
            <div class="content">
                <p class="intro-text">Answer 20 quick questions to find out your privacy risk score and get personalized
                    recommendations on what to improve.</p>
                <button id="start-btn" class="primary-btn pulse">Start Checkup <span class="arrow">→</span></button>
            </div>
        </section>

        <!-- Quiz Screen -->
        <section id="quiz-screen" class="screen">
            <header class="quiz-header">
                <div class="progress-container">
                    <div class="progress-bar" id="progress-bar"></div>
                </div>
                <div class="quiz-meta">
                    <span id="question-category" class="category-badge">Category</span>
                    <span id="question-count">Question 1 / 20</span>
                </div>
            </header>
            <div class="content quiz-content">
                <h2 id="question-text" class="question-text">Question goes here?</h2>
                <div id="options-container" class="options-container">
                    <!-- Options will be injected by JS -->
                </div>
            </div>
            <div class="quiz-footer">
                <button id="next-btn" class="secondary-btn" disabled>Next Question</button>
            </div>
        </section>

        <!-- Result Screen -->
        <section id="result-screen" class="screen">
            <header>
                <h1 class="gradient-text">Your Privacy Score</h1>
                <div class="score-display">
                    <svg class="circular-chart" viewBox="0 0 36 36">
                        <path class="circle-bg" d="M18 2.0845
                            a 15.9155 15.9155 0 0 1 0 31.831
                            a 15.9155 15.9155 0 0 1 0 -31.831" />
                        <path class="circle" id="score-circle" stroke-dasharray="0, 100" d="M18 2.0845
                            a 15.9155 15.9155 0 0 1 0 31.831
                            a 15.9155 15.9155 0 0 1 0 -31.831" />
                        <text x="18" y="20.35" class="percentage" id="score-text">0</text>
                    </svg>
                </div>
                <h2 id="score-title" class="score-title">Calculating...</h2>
                <p id="score-desc" class="score-desc">Please wait.</p>
            </header>
            <div class="content results-content">
                <div class="feedback-secton">
                    <h3>Areas to Improve</h3>
                    <div id="feedback-list" class="feedback-list">
                        <!-- Dynamic feedback -->
                    </div>
                </div>
                <button id="restart-btn" class="primary-btn mt-4">Retake Checkup</button>
            </div>
        </section>
    </main>

    <!-- Custom JS -->
    <script >
// Quiz Data based on user requirements
const quizData = [
    // Basic Privacy Awareness
    {
        id: 1,
        category: "Basic Privacy Awareness",
        question: "Do you use the same password for multiple apps or websites?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 2,
        category: "Basic Privacy Awareness",
        question: "Is two-factor authentication (OTP or authenticator app) enabled on your main accounts?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 3,
        category: "Basic Privacy Awareness",
        question: "Do you check app permissions (camera, mic, location) before installing apps?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 4,
        category: "Basic Privacy Awareness",
        question: "Have you ever clicked on a suspicious link sent on WhatsApp, email, or SMS?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 5,
        category: "Basic Privacy Awareness",
        question: "Do you regularly update your phone and apps?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },

    // Social Media Privacy
    {
        id: 6,
        category: "Social Media Privacy",
        question: "Is your social media account public or private?",
        options: [
            { text: "Public", score: 0 },
            { text: "Private", score: 1 }
        ]
    },
    {
        id: 7,
        category: "Social Media Privacy",
        question: "Do you accept follow requests from people you don’t know?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 8,
        category: "Social Media Privacy",
        question: "Have you ever shared your live location publicly on social media?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 9,
        category: "Social Media Privacy",
        question: "Do you review tagged photos/posts before they appear on your profile?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 10,
        category: "Social Media Privacy",
        question: "Do you know how to change privacy settings on your social media accounts?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },

    // Data & Security
    {
        id: 11,
        category: "Data & Security",
        question: "Do you use public Wi-Fi for banking or payments?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 12,
        category: "Data & Security",
        question: "Have you ever saved your card details on random websites?",
        options: [
            { text: "Yes", score: 0 },
            { text: "No", score: 1 }
        ]
    },
    {
        id: 13,
        category: "Data & Security",
        question: "Do you log out from accounts when using someone else’s device?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 14,
        category: "Data & Security",
        question: "Do you back up your important data (photos, documents)?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },
    {
        id: 15,
        category: "Data & Security",
        question: "Have you ever checked if your email/password was part of a data breach?",
        options: [
            { text: "Yes", score: 1 },
            { text: "No", score: 0 }
        ]
    },

    // Real Awareness Test
    {
        id: 16,
        category: "Real Awareness Test",
        question: "If you get a call asking for OTP from your bank, what will you do?",
        options: [
            { text: "Share it, as it's from the bank", score: 0 },
            { text: "Disconnect immediately and do not share", score: 1 },
            { text: "Ask them why they need it", score: 0 }
        ]
    },
    {
        id: 17,
        category: "Real Awareness Test",
        question: "What is phishing?",
        options: [
            { text: "A computer virus that deletes files", score: 0 },
            { text: "Fake emails/messages tricking you to steal info", score: 1 },
            { text: "A safe way to transfer files over network", score: 0 }
        ]
    },
    {
        id: 18,
        category: "Real Awareness Test",
        question: "Which is safer: fingerprint lock, PIN, or pattern? Why?",
        options: [
            { text: "Pattern, as it can be complex", score: 0 },
            { text: "PIN, because numbers are secure", score: 0 },
            { text: "Fingerprint/Biometric, as it's unique to you", score: 1 }
        ]
    },
    {
        id: 19,
        category: "Real Awareness Test",
        question: "What would you do if your Instagram account gets hacked?",
        options: [
            { text: "Create a new account immediately", score: 0 },
            { text: "Report to Instagram & use account recovery procedures", score: 1 },
            { text: "Wait to see if the hacker gives it back", score: 0 }
        ]
    },
    {
        id: 20,
        category: "Real Awareness Test",
        question: "Name one thing you should never share online.",
        options: [
            { text: "Your favorite food", score: 0 },
            { text: "OTP, Passwords, or exact address", score: 1 },
            { text: "Vacation photos after the trip", score: 0 }
        ]
    }
];

// State Variables
let currentQuestionIndex = 0;
let userAnswers = []; // Store chosen options

// DOM Elements
const startScreen = document.getElementById('start-screen');
const quizScreen = document.getElementById('quiz-screen');
const resultScreen = document.getElementById('result-screen');

const startBtn = document.getElementById('start-btn');
const nextBtn = document.getElementById('next-btn');
const restartBtn = document.getElementById('restart-btn');

const questionCategory = document.getElementById('question-category');
const questionCount = document.getElementById('question-count');
const progressBar = document.getElementById('progress-bar');
const questionText = document.getElementById('question-text');
const optionsContainer = document.getElementById('options-container');

const scoreCircle = document.getElementById('score-circle');
const scoreText = document.getElementById('score-text');
const scoreTitle = document.getElementById('score-title');
const scoreDesc = document.getElementById('score-desc');
const feedbackList = document.getElementById('feedback-list');

// Event Listeners
startBtn.addEventListener('click', startQuiz);
nextBtn.addEventListener('click', () => {
    if (currentQuestionIndex < quizData.length - 1) {
        currentQuestionIndex++;
        loadQuestion();
    } else {
        showResults();
    }
});
restartBtn.addEventListener('click', resetQuiz);

function switchScreen(screenElement) {
    document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
    screenElement.classList.add('active');
}

function startQuiz() {
    currentQuestionIndex = 0;
    userAnswers = [];
    switchScreen(quizScreen);
    loadQuestion();
}

function loadQuestion() {
    const questionData = quizData[currentQuestionIndex];

    // Update Header Text
    questionCategory.textContent = questionData.category;
    questionCount.textContent = `Question ${currentQuestionIndex + 1} / ${quizData.length}`;

    // Update Progress Bar
    const percent = ((currentQuestionIndex) / quizData.length) * 100;
    progressBar.style.width = `${percent}%`;

    // Set Question
    questionText.textContent = questionData.question;

    // Render Options
    optionsContainer.innerHTML = '';
    questionData.options.forEach((opt, index) => {
        const btn = document.createElement('button');
        btn.classList.add('option-btn');
        btn.textContent = opt.text;

        // Add visual click animation and logic
        btn.addEventListener('click', () => selectOption(btn, opt.score, index));
        optionsContainer.appendChild(btn);
    });

    nextBtn.disabled = true; // Disable Next until answer is selected
}

function selectOption(selectedBtn, scoreValue, optionIndex) {
    // Clear previous selection
    document.querySelectorAll('.option-btn').forEach(btn => btn.classList.remove('selected'));

    // Add selected class
    selectedBtn.classList.add('selected');

    // Save user choice
    userAnswers[currentQuestionIndex] = {
        questionId: quizData[currentQuestionIndex].id,
        category: quizData[currentQuestionIndex].category,
        score: scoreValue
    };

    // Enable Next button
    nextBtn.disabled = false;
}

function calculateCategoryScores() {
    const categoryScores = {
        "Basic Privacy Awareness": { max: 5, actual: 0 },
        "Social Media Privacy": { max: 5, actual: 0 },
        "Data & Security": { max: 5, actual: 0 },
        "Real Awareness Test": { max: 5, actual: 0 }
    };

    userAnswers.forEach(ans => {
        categoryScores[ans.category].actual += ans.score;
    });

    return categoryScores;
}

function showResults() {
    switchScreen(resultScreen);

    const totalScore = userAnswers.reduce((sum, ans) => sum + ans.score, 0);
    const maxScore = quizData.length;

    // Update Chart
    const percentage = Math.round((totalScore / maxScore) * 100);
    scoreText.textContent = `${totalScore}/${maxScore}`;

    // Change circle color based on score
    let circleColor = "var(--danger-color)"; // 0-7
    let title = "High Privacy Risk";
    let desc = "Your online safety practices need immediate attention. You are highly vulnerable to cyber threats.";

    if (totalScore >= 15) {
        circleColor = "var(--secondary-color)";
        title = "Privacy Smart User!";
        desc = "Excellent! You have a very good understanding of online privacy and security.";
    } else if (totalScore >= 8) {
        circleColor = "var(--warning-color)";
        title = "Moderate Awareness";
        desc = "You have okay privacy habits, but there are several areas where you can improve your security.";
    }

    // Delay chart animation slightly
    setTimeout(() => {
        scoreCircle.style.strokeDasharray = `${percentage}, 100`;
        scoreCircle.style.stroke = circleColor;
    }, 100);

    scoreTitle.textContent = title;
    scoreTitle.style.color = circleColor;
    scoreDesc.textContent = desc;

    // Generate Feedback
    generateFeedback(totalScore);
}

function generateFeedback(totalScore) {
    const categoryScores = calculateCategoryScores();
    feedbackList.innerHTML = '';

    const feedbacks = [];

    if (categoryScores["Basic Privacy Awareness"].actual <= 3) {
        feedbacks.push({ type: 'bad', text: "Start using a password manager and enable Two-Factor Authentication (2FA) for major accounts." });
    } else {
        feedbacks.push({ type: 'good', text: "Great job keeping basic password and authentication hygiene." });
    }

    if (categoryScores["Social Media Privacy"].actual <= 3) {
        feedbacks.push({ type: 'bad', text: "Review your social media settings. Consider making your accounts private and stop sharing live locations." });
    }

    if (categoryScores["Data & Security"].actual <= 3) {
        feedbacks.push({ type: 'bad', text: "Avoid public Wi-Fi for banking, and don't save card details on random sites." });
    }

    if (categoryScores["Real Awareness Test"].actual <= 3) {
        feedbacks.push({ type: 'bad', text: "Be highly cautious of phishing links, and never share OTPs over phone calls." });
    }

    if (totalScore === 20) {
        feedbacks.push({ type: 'good', text: "You have a flawless privacy posture! Keep staying updated." });
    }

    feedbacks.forEach(fb => {
        const div = document.createElement('div');
        div.className = `feedback-item ${fb.type}`;
        div.textContent = fb.text;
        feedbackList.appendChild(div);
    });
}

function resetQuiz() {
    progressBar.style.width = '0%';
    scoreCircle.style.strokeDasharray = '0, 100';
    startQuiz();
}

</script>
</body>

</html>
