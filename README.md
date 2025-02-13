<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Твой оракул</title>
    <style>
        /* Общие стили */
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: black; /* Черный фон */
            color: white; /* Белый текст для контраста */
            font-family: Arial, sans-serif;
        }

        /* Бегущая строка */
        #title-container {
            width: 100%;
            overflow: hidden;
            position: absolute;
            top: 20px;
        }

        #title {
            font-size: 48px;
            font-weight: bold;
            color: white;
            text-shadow: 0 0 15px purple, 0 0 30px purple;
            white-space: nowrap;
            position: relative;
            animation: marquee 8s linear infinite;
        }

        /* Анимация бегущей строки */
        @keyframes marquee {
            from { transform: translateX(100%); }
            to { transform: translateX(-100%); }
        }

        /* Кнопка "Старт" */
        #start-button {
            padding: 20px 40px;
            background-color: red;
            color: white;
            border: none;
            border-radius: 50%;
            font-size: 24px;
            cursor: pointer;
            box-shadow: 0 0 15px red;
            animation: fadeIn 1s;
        }

        /* Кнопка "Назад" */
        #back-button {
            position: absolute;
            top: 10px;
            right: 10px;
            padding: 10px;
            background-color: rgba(0, 255, 0, 0.8); /* Зеленая кнопка */
            color: white;
            border: none;
            border-radius: 50%;
            font-size: 16px;
            cursor: pointer;
            box-shadow: 0 0 10px green;
        }

        /* Зеленые кнопки с цифрами */
        .number-button {
            margin: 10px;
            padding: 15px 30px;
            background-color: green;
            color: white;
            border: none;
            border-radius: 50%;
            font-size: 20px;
            cursor: pointer;
            box-shadow: 0 0 10px green;
        }

        /* Попап с подарком */
        .popup {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            padding: 20px;
            background-color: rgba(0, 255, 0, 0.8); /* Зеленый попап */
            color: white;
            font-size: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px green;
            text-align: center;
        }

        /* Форма ввода */
        .input-field {
            margin-bottom: 10px;
            padding: 10px;
            font-size: 16px;
            border-radius: 10px;
            border: 1px solid green;
            width: 200px;
        }

        /* Кнопка отправки */
        .submit-button {
            padding: 10px 20px;
            background-color: green;
            color: white;
            border: none;
            border-radius: 50%;
            font-size: 16px;
            cursor: pointer;
            box-shadow: 0 0 10px green;
        }
    </style>
</head>
<body>
    <!-- Бегущая строка -->
    <div id="title-container">
        <div id="title">Твой оракул</div>
    </div>

    <!-- Кнопка "Старт" -->
    <button id="start-button">Старт</button>

    <!-- Скрипт -->
    <script>
        // Создание кнопки "Назад"
        function createBackButton(onClick) {
            let backButton = document.createElement('button');
            backButton.id = 'back-button';
            backButton.innerText = '<';
            backButton.addEventListener('click', onClick);
            document.body.appendChild(backButton);
        }

        // Обработчик для кнопки "Старт"
        document.getElementById('start-button').addEventListener('click', () => {
            document.body.innerHTML = ''; // Очистка страницы
            document.body.style.backgroundColor = 'black'; // Оставляем черный фон

            // Восстанавливаем бегущую строку
            let titleContainer = document.createElement('div');
            titleContainer.id = 'title-container';
            let title = document.createElement('div');
            title.id = 'title';
            title.innerText = 'Твой оракул';
            titleContainer.appendChild(title);
            document.body.appendChild(titleContainer);

            // Добавляем кнопку "Назад"
            createBackButton(() => {
                location.reload(); // Возвращаемся к начальному экрану
            });

            // Создаем кнопки с цифрами
            let numberButtonsContainer = document.createElement('div');
            numberButtonsContainer.style.display = 'flex';
            numberButtonsContainer.style.flexWrap = 'wrap';
            for (let i = 1; i <= 5; i++) {
                let numberButton = document.createElement('button');
                numberButton.className = 'number-button';
                numberButton.innerText = i;
                numberButtonsContainer.appendChild(numberButton);

                // Обработчик для каждой кнопки
                numberButton.addEventListener('click', () => {
                    // Показываем попап с сообщением
                    let popup = document.createElement('div');
                    popup.className = 'popup';
                    popup.innerText = `Вы выбрали цифру ${i}!`;

                    // Кнопка закрытия попапа
                    let closeButton = document.createElement('button');
                    closeButton.className = 'submit-button';
                    closeButton.innerText = 'Закрыть';
                    closeButton.addEventListener('click', () => {
                        document.body.removeChild(popup);
                    });
                    popup.appendChild(closeButton);

                    document.body.appendChild(popup);
                });
            }
            document.body.appendChild(numberButtonsContainer);
        });
    </script>
</body>
</html>
