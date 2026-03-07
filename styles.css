document.addEventListener("DOMContentLoaded", function() {

    // --- Feather Icons Replacement ---
    feather.replace();

    // --- Animate On Scroll (AOS) Initialization ---
    AOS.init({
        duration: 800,
        once: true,
        offset: 50,
    });

    // --- Mobile Navigation (Hamburger Menu) ---
    const hamburger = document.querySelector(".hamburger");
    const navMenu = document.querySelector(".nav-menu");
    const navLinks = document.querySelectorAll(".nav-link");

    if (hamburger && navMenu) {
        hamburger.addEventListener("click", () => {
            hamburger.classList.toggle("active");
            navMenu.classList.toggle("active");
            document.body.style.overflow = navMenu.classList.contains("active") ? "hidden" : "auto";
        });
    }

    navLinks.forEach(link => {
        link.addEventListener("click", () => {
            if (hamburger && navMenu && navMenu.classList.contains("active")) {
                hamburger.classList.remove("active");
                navMenu.classList.remove("active");
                document.body.style.overflow = "auto";
            }
        });
    });

    // --- Certificate Carousel & Modal ---
    const certificateFiles = [
        "publication certificate for KrishiDIsha.png",
        "publication certificate for Student Dropout.jpeg",
        "codevir competiton certificate.jpeg",
        "tittle competition certificate.jpeg",
        "certificate1.png", "certificate2.png", "certificate3.png",
        "certificate4.png", "certificate5.png", "certificate6.png",
        "certificate7.png", "certificate8.png", "certificate9.png",
        "certificate10.png", "certificate11.png", "certificate12.png",
        "certificate13.png"
    ];

    const carousel = document.getElementById('certificate-carousel');
    const modal = document.getElementById('certificate-modal');
    const modalImg = document.getElementById('modal-image');
    const closeModalBtn = document.querySelector('.close-modal');

    if (carousel && certificateFiles.length > 0) {
        let autoScrollInterval;
        let inactivityTimer;

        const populateCarousel = () => {
            carousel.innerHTML = '';
            const allFiles = [...certificateFiles, ...certificateFiles]; // Duplicate for seamless loop

            allFiles.forEach(file => {
                const item = document.createElement('div');
                item.className = 'certificate-item';

                const img = document.createElement('img');
                const imgPath = `img/${file}`;
                img.src = imgPath;
                img.alt = 'Certificate Preview';
                img.loading = 'lazy';
                img.decoding = 'async';

                img.onerror = () => {
                    console.warn(`Could not load certificate image: ${imgPath}. Displaying placeholder.`);
                    const placeholderText = file.split('.')[0].replace(/_/g, ' ').substring(0, 20);
                    img.src = `https://placehold.co/400x300/191924/A1A1A6?text=${encodeURIComponent(placeholderText)}`;
                    img.onerror = null;
                };

                item.appendChild(img);

                item.addEventListener('click', () => {
                    if (modal && modalImg) {
                        modal.style.display = 'flex';
                        modalImg.src = img.src;
                    }
                });
                carousel.appendChild(item);
            });
        };

        populateCarousel();

        const startAutoScroll = () => {
            clearInterval(autoScrollInterval);
            autoScrollInterval = setInterval(() => {
                if (carousel.scrollLeft >= carousel.scrollWidth / 2) {
                    carousel.scrollLeft = 0;
                }
                carousel.scrollLeft += 1;
            }, 20);
        };

        const stopAutoScroll = () => {
            clearInterval(autoScrollInterval);
        };

        const resetInactivityTimer = () => {
            clearTimeout(inactivityTimer);
            inactivityTimer = setTimeout(() => {
                startAutoScroll();
            }, 5000);
        };

        const prevBtn = document.querySelector('.prev-btn');
        const nextBtn = document.querySelector('.next-btn');

        if (prevBtn && nextBtn) {
            prevBtn.addEventListener('click', () => {
                stopAutoScroll();
                const scrollAmount = carousel.children[0].offsetWidth + 20;
                carousel.scrollBy({ left: -scrollAmount, behavior: 'smooth' });
                resetInactivityTimer();
            });

            nextBtn.addEventListener('click', () => {
                stopAutoScroll();
                const scrollAmount = carousel.children[0].offsetWidth + 20;
                carousel.scrollBy({ left: scrollAmount, behavior: 'smooth' });
                resetInactivityTimer();
            });
        }

        const carouselContainer = document.querySelector('.certificate-carousel-container');
        if (carouselContainer) {
            carouselContainer.addEventListener('mouseenter', stopAutoScroll);
            carouselContainer.addEventListener('mouseleave', () => {
                resetInactivityTimer();
                startAutoScroll();
            });
        }
        
        startAutoScroll();
        feather.replace();
    }

    const hideModal = () => {
        if (modal) modal.style.display = 'none';
    };

    if (closeModalBtn) closeModalBtn.addEventListener('click', hideModal);
    if (modal) modal.addEventListener('click', (e) => {
        if (e.target === modal) hideModal();
    });
    document.addEventListener('keydown', (e) => {
        if (e.key === "Escape") hideModal();
    });

    // --- Theme Toggle (Light/Dark Mode) ---
    const themeToggleButton = document.getElementById('theme-toggle');
    const body = document.body;

    const setTheme = (theme) => {
        body.className = theme;
        const themeIcon = themeToggleButton.querySelector('i');
        if (themeIcon) {
            themeIcon.setAttribute('data-feather', theme === 'light-mode' ? 'sun' : 'moon');
            feather.replace();
        }
        localStorage.setItem('theme', theme);
    };

    if (themeToggleButton) {
        themeToggleButton.addEventListener('click', () => {
            const newTheme = body.classList.contains('light-mode') ? 'dark-mode' : 'light-mode';
            setTheme(newTheme);
        });
    }

    const savedTheme = localStorage.getItem('theme') || 'dark-mode';
    setTheme(savedTheme);

    // --- Dynamic Card Glow Effect (for non-touch devices) ---
    const isTouchDevice = () => 'ontouchstart' in window || navigator.maxTouchPoints > 0;

    if (!isTouchDevice()) {
        document.querySelectorAll('.project-card, .publication-card').forEach(card => {
            card.addEventListener('mousemove', e => {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                card.style.setProperty('--x', `${x}px`);
                card.style.setProperty('--y', `${y}px`);
            });
        });
    }

    // --- Contact Form Mailto Logic ---
    const subjectInput = document.getElementById('subject');
    const messageTextarea = document.getElementById('message');
    const mailtoLink = document.getElementById('send-email-btn');
    const recipientInput = document.getElementById('recipient');

    if (subjectInput && messageTextarea && mailtoLink && recipientInput) {
        const recipient = recipientInput.value;

        const updateMailtoLink = () => {
            const subject = encodeURIComponent(subjectInput.value);
            const message = encodeURIComponent(messageTextarea.value);
            // This is the updated line for Gmail
            mailtoLink.href = `https://mail.google.com/mail/?view=cm&fs=1&to=${recipient}&su=${subject}&body=${message}`;
        };

        subjectInput.addEventListener('input', updateMailtoLink);
        messageTextarea.addEventListener('input', updateMailtoLink);

        updateMailtoLink();
    }


    // --- Chatbot Logic ---
    const chatbotIcon = document.getElementById('chatbot-icon');
    const chatbotWindow = document.getElementById('chatbot-window');
    const closeChatbotBtn = document.getElementById('close-chatbot');
    const chatbotForm = document.getElementById('chatbot-form');
    const chatbotInput = document.getElementById('chatbot-input');
    const chatbotMessages = document.getElementById('chatbot-messages');
    
    // --- UPDATED KNOWLEDGE BASE ---
    const knowledgeBase = {
        "hello": "Hi there! How can I help you learn more about Abhishek?",
        "hi": "Hello! Feel free to ask me about Abhishek's skills, projects, or experience.",
        "who are you": "I am an AI assistant designed to answer questions about Abhishek Chourasia's portfolio.",
        "name": "His name is Abhishek Chourasia.",
        "contact": "You can reach Abhishek at +91 9752950569 or abhishekchourasia29122003@email.com. His Portfolio, LinkedIn, and GitHub profiles are also available.",
        "summary": "Abhishek is a B.Tech. Computer Science graduate from Medi-Caps University with a 9.33 CGPA, specializing in AI, Machine Learning, and Full-Stack Development. His experience includes engineering end-to-end AI systems like multi-agent chatbots and agentic systems at Supersourcing and creating a breast cancer detection tool under IBM's mentorship. He is also a published researcher with papers in IEEE and Springer Nature.",
        "skills": "Abhishek's technical skills include Languages & Databases like Python, Java, C/C++, JavaScript, HTML/CSS, SQL, MongoDB, and PostgreSQL. He is proficient in Frameworks & Tools such as LangChain, LangGraph, FastAPI, Flask, Django, Scikit-learn, TensorFlow, Pandas, NumPy, Git, and Docker. His core competencies are in Machine Learning, Deep Learning (CNN, RNN-LSTM), LLMs, RAG, Agentic Workflows, Full Stack Web Development, Data Analysis, and Research & Development.",
        "experience": "Abhishek is an AI/ML Intern at Supersourcing from July 2025 to the present, where he enhanced the SuperGPT enterprise chatbot. He was also a Machine Learning Research Intern at IBM Global Remote Mentorship from July 2024 to December 2024, where he developed 'Web-BCD', a breast cancer detection system.",
        "education": "Abhishek earned his B.Tech in Computer Science from Medi-Caps University (August 2023-May 2025) with a CGPA of 9.33. Prior to that, he completed a B.Sc in Computer Science (AIML) from the same university (June 2021-July 2023) with an 8.88 CGPA. He completed his 12th standard with 86.2% in 2021 and 10th standard with 85.4% in 2019 from Karnataka Vidya Niketan School.",
        "projects": "He has worked on several projects, including the 'A-Prime-Al Multi-Agent Chatbot Platform', 'SuperGPT Enterprise Al Agent Enhancement', the 'Krishi Disha Al-driven Crop Optimization Platform', and 'STUDROP Student Dropout Analysis using ML/DL'. Which one would you like to know more about?",
        "a-prime-ai": "A-Prime-Al is a multi-agent chatbot platform Abhishek has been developing since May 2025. It uses a FastAPI backend and an intelligent routing system to delegate tasks to specialized agents for web search, image generation, code creation, and Q&A. It integrates APIs like Tavily, Stability Al, and Groq, and uses MongoDB for persistent memory.",
        "supergpt": "As part of his internship at Supersourcing, Abhishek enhanced the SuperGPT enterprise chatbot. He engineered a role-based access control agent and a conversational agent for team dashboards. He also upgraded the core logic to support multi-agent workflows using Python, Langchain, Langraph, and FastAPI.",
        "krishidisha": "KrishiDisha is an AI-driven platform for agriculture that Abhishek worked on from October 2024 to April 2025. It provides crop/fertilizer recommendations, disease detection, and yield prediction using Machine Learning models. It also features an AI-powered multilingual chatbot and was deployed using Flask. A paper on this project was accepted for the 2025 ICOEIT conference.",
        "studrop": "STUDROP is a project on student dropout analysis using ML/DL that Abhishek worked on from October 2023 to January 2024. He co-authored and presented a paper on this work at WCSC 2024, which was published by Springer Nature in April 2025.",
        "publications": "Abhishek has two publications. One is a paper titled 'KrishiDisha: Revolutionizing Agriculture...' accepted for the 2025 International Conference on Engineering Innovations and Technologies (ICOEIT). The other is a paper on student dropout analysis published by Springer Nature in the Studies in Smart Technologies series.",
        "cgpa": "Abhishek's CGPA in his B.Tech in Computer Science is 9.33.",
        "percentage_10th": "Abhishek's 10th standard percentage is 85.4%.",
        "percentage_12th": "Abhishek's 12th standard percentage is 86.2%.",
        "school_name": "Abhishek's school name is Karnataka Vidya Niketan.",
        "university_name": "Abhishek completed his B.Tech in CSE from Medi-Caps University, Indore.",
        "college_name": "Abhishek completed his B.Tech in CSE from Medi-Caps University, Indore.",
        "internship": "At Supersourcing, he is an AI/ML Intern enhancing the SuperGPT chatbot. He was previously a Machine Learning Research Intern with IBM, where he developed Web-BCD, a breast cancer detection system, using Python, Scikit-learn, and a Sequential Neural Network, and deployed it with Flask.",
        "certifications": "Abhishek holds certifications in Academic Process Mining Fundamentals from Celonis, Data Science & Machine Learning with Python from IBM, Python for Data Science from NPTEL IIT Madras, and Python Essentials, Networking Essentials, & OS Basics from Cisco.",
        "awards": "He achieved an All India Rank of 17 in CodeVir from iNurture Education Solutions in July 2024 and was a Runner-Up (Silver Medalist) in the National Transtemporal Tattle Trials in July 2024 & July 2023.",
        "thank": "You're welcome! Is there anything else I can help you with?",
        "bye": "Goodbye! Have a great day."
    };

    // --- EFFICIENT BOT RESPONSE LOGIC ---
    const getBotResponse = (userInput) => {
        const lowerInput = userInput.toLowerCase().trim();

        // 1. Check for an exact match (fastest)
        if (knowledgeBase[lowerInput]) {
            return knowledgeBase[lowerInput];
        }

        // 2. Use a keyword map for efficient and specific matching
        const keywordMap = {
            '10th score': 'percentage_10th',
            '10th percentage': 'percentage_10th',
            '12th score': 'percentage_12th',
            '12th percentage': 'percentage_12th',
            'school name': 'school_name',
            'college name': 'college_name',
            'university name': 'university_name',
            'work experience': 'experience',
            'educational background': 'education',
            'supersourcing': 'supergpt',
            'ibm': 'internship',
            'a-prime-ai': 'a-prime-ai',
            'a-prime-al': 'a-prime-ai',
            'krishidisha': 'krishidisha',
            'studrop': 'studrop',
            'school': 'school_name',
            'college': 'college_name',
            'university': 'university_name'
        };

        let bestMatchKey = null;
        let highestScore = 0;

        for (const keyword in keywordMap) {
            if (lowerInput.includes(keyword) && keyword.length > highestScore) {
                highestScore = keyword.length;
                bestMatchKey = keywordMap[keyword];
            }
        }

        if (bestMatchKey) {
            return knowledgeBase[bestMatchKey];
        }
        
        // 3. Broad fallback search if no specific keyword is found
        for (const key in knowledgeBase) {
            if (lowerInput.includes(key) && key.length > highestScore) {
                highestScore = key.length;
                bestMatchKey = key;
            }
        }
        
        if (bestMatchKey) {
            return knowledgeBase[bestMatchKey];
        }

        // 4. Default fallback response
        return "I'm sorry, I don't have information on that. Try asking about skills, projects, or experience.";
    };


    const addMessage = (text, sender) => {
        const messageElement = document.createElement('div');
        messageElement.className = `chat-message ${sender}`;
        messageElement.textContent = text;
        chatbotMessages.appendChild(messageElement);
        chatbotMessages.scrollTop = chatbotMessages.scrollHeight;
    };

    if (chatbotIcon) {
        chatbotIcon.addEventListener('click', () => {
            chatbotWindow.classList.toggle('hidden');
            if (!chatbotWindow.classList.contains('hidden')) {
                feather.replace();
            }
        });
    }

    if (closeChatbotBtn) {
        closeChatbotBtn.addEventListener('click', () => {
            chatbotWindow.classList.add('hidden');
        });
    }

    if (chatbotForm) {
        chatbotForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const userInput = chatbotInput.value.trim();
            if (userInput === '') return;

            addMessage(userInput, 'user');
            chatbotInput.value = '';

            setTimeout(() => {
                const botResponse = getBotResponse(userInput);
                addMessage(botResponse, 'bot');
            }, 500);
        });
    }
    if (document.getElementById('typed-text')) {
        new Typed('#typed-text', {
            strings: [
                'B.Tech. Computer Science Student',
                'AI &amp; ML Engineer',
                'Full Stack Developer',
                'Published Researcher'
            ],
            typeSpeed: 50,
            backSpeed: 30,
            backDelay: 2000,
            startDelay: 500,
            loop: true
        });
    }

    // --- Enhanced Smooth Scrolling with Header Offset ---
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
        anchor.addEventListener('click', function (e) {
            e.preventDefault();
            const targetId = this.getAttribute('href');
            
            // Special case for the logo/home link to just go to the top
            if (targetId === '#hero') {
                 window.scrollTo({
                    top: 0,
                    behavior: 'smooth'
                });
                 // Close mobile menu if open
                if (hamburger && navMenu && navMenu.classList.contains("active")) {
                    hamburger.classList.remove("active");
                    navMenu.classList.remove("active");
                    document.body.style.overflow = "auto";
                }
                return;
            }

            const targetElement = document.querySelector(targetId);

            if (targetElement) {
                const headerOffset = document.querySelector('.main-header').offsetHeight;
                const elementPosition = targetElement.getBoundingClientRect().top;
                const offsetPosition = elementPosition + window.pageYOffset - headerOffset;

                window.scrollTo({
                    top: offsetPosition,
                    behavior: "smooth"
                });
            }
        });
    });


    // --- Scroll to Top Button Logic ---
    const scrollTopBtn = document.getElementById('scrollTopBtn');

    if (scrollTopBtn) {
        window.addEventListener('scroll', () => {
            if (window.scrollY > 300) {
                scrollTopBtn.classList.add('visible');
            } else {
                scrollTopBtn.classList.remove('visible');
            }
        });
        
        feather.replace();
    }
});
