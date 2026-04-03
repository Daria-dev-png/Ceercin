<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🧸 Бюджетный детский сад</title>
    
    <!-- Шрифт Montserrat -->
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Bootstrap 5 CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Bootstrap Icons -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.1/font/bootstrap-icons.css" rel="stylesheet">
    
    <style>
        /* Шрифт для всего сайта */
        body { 
            font-family: 'Montserrat', sans-serif; 
        }
        h1, h2, h3, h4, h5, .navbar-brand, .btn, .card-title {
            font-family: 'Montserrat', sans-serif;
        }
        
        /* Игровые элементы */
        .monster-avatar { 
            font-size: 4rem; 
            cursor: pointer; 
            transition: transform 0.2s; 
        }
        .monster-avatar:active { 
            transform: scale(0.95); 
        }
        .coin { animation: bounce 0.6s ease; }
        @keyframes bounce { 
            0%, 100% { transform: translateY(0); } 
            50% { transform: translateY(-20px); } 
        }
        .budget-bar { height: 25px; border-radius: 15px; }
        
        /* Лёгкие эффекты для карточек */
        .card {
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .card:hover {
            transform: translateY(-4px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1) !important;
        }
    </style>
</head>
<body class="bg-light">

    <!-- Навигация -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary sticky-top shadow-sm">
        <div class="container">
            <a class="navbar-brand fw-bold" href="#">
                <i class="bi bi-piggy-bank-fill me-2"></i>Бюджетный детский сад
            </a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav me-auto">
                    <li class="nav-item"><a class="nav-link active" href="#">🏠 Главная</a></li>
                    <li class="nav-item"><a class="nav-link" href="#spending">💰 Куда идут деньги</a></li>
                    <li class="nav-item"><a class="nav-link" href="#about">❓ Как это работает</a></li>
                </ul>
                <div class="d-flex align-items-center">
                    <span class="text-white me-3 d-none d-md-block">Собрано налогов:</span>
                    <span class="badge bg-warning text-dark fs-6 px-3 py-2" id="taxCounter">0 ₽</span>
                </div>
            </div>
        </div>
    </nav>

    <!-- Герой-секция с каруселью -->
    <div class="container mt-4">
        <div class="row">
            <div class="col-12">
                <div id="heroCarousel" class="carousel slide rounded-3 shadow" data-bs-ride="carousel">
                    <div class="carousel-indicators">
                        <button type="button" data-bs-target="#heroCarousel" data-bs-slide-to="0" class="active"></button>
                        <button type="button" data-bs-target="#heroCarousel" data-bs-slide-to="1"></button>
                        <button type="button" data-bs-target="#heroCarousel" data-bs-slide-to="2"></button>
                    </div>
                    <div class="carousel-inner">
                        <div class="carousel-item active">
                            <div class="bg-primary bg-gradient text-white p-5 text-center rounded-3">
                                <h1 class="display-5 fw-bold">🎪 Добро пожаловать!</h1>
                                <p class="lead mb-4">Узнай, как налоги превращаются в детские сады, школы и парки!</p>
                                <button class="btn btn-light btn-lg fw-bold" data-bs-toggle="modal" data-bs-target="#howItWorks">
                                    <i class="bi bi-play-circle me-2"></i>Как это работает?
                                </button>
                            </div>
                        </div>
                        <div class="carousel-item">
                            <div class="bg-success bg-gradient text-white p-5 text-center rounded-3">
                                <h1 class="display-5 fw-bold">👾 Познакомься с Бюджетиком!</h1>
                                <p class="lead mb-4">Он любит "кушать" налоги и "выплевывать" бюджет на добрые дела!</p>
                                <span class="monster-avatar">👾</span>
                            </div>
                        </div>
                        <div class="carousel-item">
                            <div class="bg-info bg-gradient text-white p-5 text-center rounded-3">
                                <h1 class="display-5 fw-bold">🎯 Твоя миссия</h1>
                                <p class="lead mb-4">Покорми Бюджетика налогами — и он построит новую площадку!</p>
                                <button class="btn btn-light btn-lg fw-bold" onclick="feedMonster()">
                                    <i class="bi bi-currency-ruble me-2"></i>Покормить монстра!
                                </button>
                            </div>
                        </div>
                    </div>
                    <button class="carousel-control-prev" type="button" data-bs-target="#heroCarousel" data-bs-slide="prev">
                        <span class="carousel-control-prev-icon"></span>
                    </button>
                    <button class="carousel-control-next" type="button" data-bs-target="#heroCarousel" data-bs-slide="next">
                        <span class="carousel-control-next-icon"></span>
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Основной контент с карточками -->
    <div class="container mt-5" id="spending">
        <div class="row mb-4">
            <div class="col-12 text-center">
                <h2 class="fw-bold text-primary">🎁 На что пошли наши деньги?</h2>
                <p class="text-muted">Нажми на карточку, чтобы узнать подробности!</p>
            </div>
        </div>

        <div class="row g-4">
            <!-- Карточка 1: Школа -->
            <div class="col-12 col-md-6 col-lg-4">
                <div class="card h-100 shadow-sm border-0">
                    <img src="школа.jpg" class="card-img-top img-fluid rounded-top" alt="Школа">
                    <div class="card-body">
                        <h5 class="card-title fw-bold text-primary">🏫 Новая школа</h5>
                        <p class="card-text">Современные классы, компьютеры и спортзал для детей!</p>
                        <div class="progress mb-3" style="height: 10px;">
                            <div class="progress-bar bg-success" role="progressbar" style="width: 75%">75%</div>
                        </div>
                        <button class="btn btn-outline-primary w-100" data-bs-toggle="modal" data-bs-target="#schoolModal">
                            <i class="bi bi-info-circle me-1"></i>Подробнее
                        </button>
                    </div>
                    <div class="card-footer bg-white border-0">
                        <small class="text-muted"><i class="bi bi-check-circle-fill text-success me-1"></i>Финансируется из бюджета</small>
                    </div>
                </div>
            </div>

            <!-- Карточка 2: Больница -->
            <div class="col-12 col-md-6 col-lg-4">
                <div class="card h-100 shadow-sm border-0">
                    <img src="больница.png" class="card-img-top img-fluid rounded-top" alt="Больница">
                    <div class="card-body">
                        <h5 class="card-title fw-bold text-danger">🏥 Детская поликлиника</h5>
                        <p class="card-text">Бесплатные врачи, прививки и современное оборудование.</p>
                        <div class="progress mb-3" style="height: 10px;">
                            <div class="progress-bar bg-info" role="progressbar" style="width: 90%">90%</div>
                        </div>
                        <button class="btn btn-outline-danger w-100" data-bs-toggle="modal" data-bs-target="#hospitalModal">
                            <i class="bi bi-info-circle me-1"></i>Подробнее
                        </button>
                    </div>
                    <div class="card-footer bg-white border-0">
                        <small class="text-muted"><i class="bi bi-check-circle-fill text-success me-1"></i>Финансируется из бюджета</small>
                    </div>
                </div>
            </div>

            <!-- Карточка 3: Парк ✅ ИСПРАВЛЕНО -->
            <div class="col-12 col-md-6 col-lg-4">
                <div class="card h-100 shadow-sm border-0">
                    <img src="парк.webp" class="card-img-top img-fluid rounded-top" alt="Парк">
                    <div class="card-body">
                        <h5 class="card-title fw-bold text-success">🌳 Парк с площадкой</h5>
                        <!-- 🔧 Исправлено: был пропущен открывающий тег <p> -->
                        <p class="card-text">Безопасные горки, качели и зелёные зоны для прогулок.</p>
                        <div class="progress mb-3" style="height: 10px;">
                            <div class="progress-bar bg-warning" role="progressbar" style="width: 60%">60%</div>
                        </div>
                        <button class="btn btn-outline-success w-100" data-bs-toggle="modal" data-bs-target="#parkModal">
                            <i class="bi bi-info-circle me-1"></i>Подробнее
                        </button>
                    </div>
                    <div class="card-footer bg-white border-0">
                        <small class="text-muted"><i class="bi bi-check-circle-fill text-success me-1"></i>Финансируется из бюджета</small>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Интерактивная зона с монстром -->
    <div class="container mt-5 py-4 bg-white rounded-3 shadow-sm">
        <div class="row align-items-center">
            <div class="col-lg-6 text-center mb-4 mb-lg-0">
                <div class="monster-avatar display-1" id="monster" onclick="feedMonster()">👾</div>
                <p class="mt-3 text-muted small">Нажми на монстра, чтобы "покормить" его налогом!</p>
                <button class="btn btn-warning btn-lg fw-bold shadow" onclick="feedMonster()">
                    <i class="bi bi-currency-ruble me-2"></i>Дать 100 ₽
                </button>
            </div>
            <div class="col-lg-6">
                <h4 class="fw-bold mb-3">📊 Визуализация бюджета</h4>
                
                <div class="mb-3">
                    <div class="d-flex justify-content-between mb-1">
                        <span>🏫 Школы</span>
                        <span class="fw-bold">45%</span>
                    </div>
                    <div class="progress budget-bar">
                        <div class="progress-bar bg-primary" style="width: 45%"></div>
                    </div>
                </div>
                
                <div class="mb-3">
                    <div class="d-flex justify-content-between mb-1">
                        <span>🏥 Медицина</span>
                        <span class="fw-bold">30%</span>
                    </div>
                    <div class="progress budget-bar">
                        <div class="progress-bar bg-danger" style="width: 30%"></div>
                    </div>
                </div>
                
                <div class="mb-3">
                    <div class="d-flex justify-content-between mb-1">
                        <span>🌳 Парки и спорт</span>
                        <span class="fw-bold">15%</span>
                    </div>
                    <div class="progress budget-bar">
                        <div class="progress-bar bg-success" style="width: 15%"></div>
                    </div>
                </div>
                
                <div class="mb-3">
                    <div class="d-flex justify-content-between mb-1">
                        <span>🔧 Прочее</span>
                        <span class="fw-bold">10%</span>
                    </div>
                    <div class="progress budget-bar">
                        <div class="progress-bar bg-secondary" style="width: 10%"></div>
                    </div>
                </div>
                
                <div class="alert alert-info mt-4 mb-0">
                    <i class="bi bi-lightbulb me-2"></i>
                    <strong>Знаешь ли ты?</strong> Каждый рубль налогов возвращается тебе в виде бесплатных услуг!
                </div>
            </div>
        </div>
    </div>

    <!-- Модальные окна -->
    
    <!-- Модальное окно: Как это работает -->
    <div class="modal fade" id="howItWorks" tabindex="-1">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-header bg-primary text-white">
                    <h5 class="modal-title">🔄 Как работает бюджет?</h5>
                    <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body">
                    <ol class="list-group list-group-flush">
                        <li class="list-group-item">👨‍👩‍👧‍👦 Люди платят налоги государству</li>
                        <li class="list-group-item">👾 Бюджетик "съедает" налоги</li>
                        <li class="list-group-item">💰 Деньги идут в бюджет</li>
                        <li class="list-group-item">🏫🏥🌳 Бюджет строит школы, больницы, парки</li>
                        <li class="list-group-item">😊 Все довольны!</li>
                    </ol>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-primary" data-bs-dismiss="modal">Понял! 🎉</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Модальное окно: Школа -->
    <div class="modal fade" id="schoolModal" tabindex="-1">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">🏫 Новая школа</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body">
                    <img src="школа.jpg" class="img-fluid rounded mb-3" alt="Школа">
                    <p>На строительство этой школы было выделено <strong>150 млн ₽</strong> из бюджета.</p>
                    <ul>
                        <li>25 современных классов</li>
                        <li>Компьютерная лаборатория</li>
                        <li>Спортивный зал и стадион</li>
                        <li>Бесплатное питание для учеников</li>
                    </ul>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Закрыть</button>
                    <button type="button" class="btn btn-primary">🎒 Хочу учиться здесь!</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Модальное окно: Больница -->
    <div class="modal fade" id="hospitalModal" tabindex="-1">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">🏥 Детская поликлиника</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body">
                    <img src="больница.png" class="img-fluid rounded mb-3" alt="Больница">
                    <p>Бюджет выделил <strong>80 млн ₽</strong> на современное оборудование.</p>
                    <ul>
                        <li>Бесплатный приём педиатра</li>
                        <li>Вакцинация по календарю прививок</li>
                        <li>Новое диагностическое оборудование</li>
                        <li>Комфортные палаты для малышей</li>
                    </ul>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Закрыть</button>
                    <button type="button" class="btn btn-danger">❤️ Спасибо врачам!</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Модальное окно: Парк -->
    <div class="modal fade" id="parkModal" tabindex="-1">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">🌳 Парк с площадкой</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body">
                    <img src="парк.webp" class="img-fluid rounded mb-3" alt="Парк">
                    <p>На благоустройство парка потрачено <strong>25 млн ₽</strong>.</p>
                    <ul>
                        <li>Безопасные детские площадки</li>
                        <li>Зелёные зоны и скамейки</li>
                        <li>Освещение и видеонаблюдение</li>
                        <li>Бесплатный вход для всех!</li>
                    </ul>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Закрыть</button>
                    <button type="button" class="btn btn-success">🛝 Хочу на площадку!</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Футер -->
    <footer class="bg-dark text-white py-4 mt-5">
        <div class="container text-center">
            <p class="mb-1">🧸 Бюджетный детский сад — учимся понимать бюджет с детства!</p>
            <p class="small text-muted mb-0">
                Источники данных: 
                <a href="https://budget.gov.ru" class="text-white-50 text-decoration-none" target="_blank">budget.gov.ru</a> | 
                <a href="https://minfin.gov.ru" class="text-white-50 text-decoration-none" target="_blank">minfin.gov.ru</a>
            </p>
            <small class="text-muted">© 2024 Практическая работа по Bootstrap 5</small>
        </div>
    </footer>

    <!-- Bootstrap JS Bundle -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
    
    <!-- Интерактив: звуки и анимация -->
    <script>
        let taxTotal = 0;
        const taxCounter = document.getElementById('taxCounter');
        const monster = document.getElementById('monster');
        const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        
        function playSound(type) {
            if (audioCtx.state === 'suspended') audioCtx.resume();
            const oscillator = audioCtx.createOscillator();
            const gainNode = audioCtx.createGain();
            oscillator.connect(gainNode);
            gainNode.connect(audioCtx.destination);
            
            if (type === 'click') {
                oscillator.frequency.value = 800;
                gainNode.gain.value = 0.1;
                oscillator.type = 'sine';
                oscillator.start();
                oscillator.stop(audioCtx.currentTime + 0.1);
            } else if (type === 'coin') {
                oscillator.frequency.setValueAtTime(600, audioCtx.currentTime);
                oscillator.frequency.exponentialRampToValueAtTime(1200, audioCtx.currentTime + 0.15);
                gainNode.gain.value = 0.15;
                oscillator.type = 'triangle';
                oscillator.start();
                oscillator.stop(audioCtx.currentTime + 0.2);
            } else if (type === 'applause') {
                oscillator.frequency.value = 400;
                gainNode.gain.value = 0.05;
                oscillator.type = 'square';
                oscillator.start();
                oscillator.stop(audioCtx.currentTime + 0.3);
            }
        }
        
        function feedMonster() {
            playSound('click');
            monster.classList.add('coin');
            setTimeout(() => monster.classList.remove('coin'), 600);
            taxTotal += 100;
            taxCounter.textContent = taxTotal.toLocaleString('ru-RU') + ' ₽';
            playSound('coin');
            
            if (taxTotal >= 500) {
                setTimeout(() => {
                    playSound('applause');
                    alert('🎉 Ура! Ты собрал 500 ₽! Бюджетик строит новую площадку! 🎠');
                }, 300);
            }
        }
        
        document.querySelectorAll('button, .nav-link, .carousel-control-prev, .carousel-control-next').forEach(btn => {
            btn.addEventListener('click', () => playSound('click'));
        });
    </script>
</body>
</html>
