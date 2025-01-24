// Array to hold quiz data (for demo purposes, you would normally fetch this from a server)
const quizzes = [
    { id: 1, title: "JavaScript Basics", description: "Test your JS knowledge" },
    { id: 2, title: "HTML & CSS Quiz", description: "Learn web development!" }
];

// Function to load quizzes dynamically on quiz listing page
function loadQuizzes() {
    const quizListContainer = document.querySelector('.quiz-list');
    quizListContainer.innerHTML = ''; // Clear existing quizzes

    quizzes.forEach(quiz => {
        const quizItem = document.createElement('div');
        quizItem.classList.add('quiz-item');
        quizItem.innerHTML = `
            <h3>${quiz.title}</h3>
            <p>${quiz.description}</p>
            <button onclick="startQuiz(${quiz.id})">Take Quiz</button>
        `;
        quizListContainer.appendChild(quizItem);
}

// Display quizzes when the quizzes page is loaded 
 if (window.location.pathname.includes('quizzes.html')) {
    loadQuizzes();
}

// Function to start a quiz (populate questions dynamically)
function startQuiz(quizId) {
    const quiz = quizzes.find(q => q.id === quizId);
    document.getElementById('quiz-questions').innerHTML = ''; // Clear existing questions

    // Hardcoded questions for the demo. You can fetch real data here.
    const questions = [
        { question: "What does 'JS' stand for?", options: ["JavaScript", "JScript", "JavaScripting", "None of the above"], answer: "JavaScript" },
        { question: "Which HTML element is used to define an internal style sheet?", options: ["<style>", "<css>", "<script>", "<head>"], answer: "<style>" },
    ];

    // Add the questions to the page dynamically
    questions.forEach((q, index) => {
        const questionDiv = document.createElement('div');
        questionDiv.classList.add('question');
        questionDiv.innerHTML = `
            <label>${q.question}</label>
            <div class="options">
                ${q.options.map((opt, i) => `
                    <input type="radio" name="q${index}" value="${opt}" id="q${index}a${i}"> ${opt}
                `).join('')}
            </div>
        `;
        document.getElementById('quiz-questions').appendChild(questionDiv);
    });

    // Redirect the user to the quiz-taking page
    window.location.href = 'take-quiz.html';
}

// Handle form submission for quiz creation
document.getElementById('quiz-form')?.addEventListener('submit', function(e){
    e.preventDefault();

    const quizTitle = document.getElementById('quiz-title').value;
    const quizDescription = document.getElementById('quiz-description').value;
    alert('Quiz Created: ' + quizTitle + ' - ' + quizDescription);

    // Normally, you would save this to the database here
    window.location.href = 'quizzes.html';
});

// Handle form submission for quiz taking
document.getElementById('quiz-taker-form')?.addEventListener('submit', function(e) {
    e.preventDefault();
    
    const formData = new FormData(e.target);
    let score = 0;

    // For demo purposes, we'll assume the answers are predefined and check them
    if (formData.get('q0') === 'JavaScript') score++;
    if (formData.get('q1') === '<style>') score++;

    alert(`Your Score: ${score}`);
})
