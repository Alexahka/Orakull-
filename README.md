// Устанавливаем стиль для body
document.body.style.margin = 0;
document.body.style.padding = 0;
document.body.style.overflow = 'hidden';
document.body.style.display = 'flex';
document.body.style.flexDirection = 'column';
document.body.style.alignItems = 'center';
document.body.style.justifyContent = 'center';
document.body.style.height = '100vh';
document.body.style.backgroundColor = 'black';

// Создание бегущей строки "Твой оракул"
let titleContainer = document.createElement('div');
titleContainer.style.width = '100%';
titleContainer.style.overflow = 'hidden';
titleContainer.style.position = 'absolute';
titleContainer.style.top = '20px';
let title = document.createElement('div');
title.innerText = 'Твой оракул';
title.style.fontSize = '48px';
title.style.fontWeight = 'bold';
title.style.color = 'white';
title.style.textShadow = '0 0 15px purple, 0 0 30px purple';
title.style.whiteSpace = 'nowrap';
title.style.position = 'relative';
title.style.animation = 'marquee 8s linear infinite';
titleContainer.appendChild(title);
document.body.appendChild(titleContainer);

// Добавление анимации бегущей строки
let style = document.createElement('style');
style.innerHTML = `
    @keyframes marquee {
        from { transform: translateX(100%); }
        to { transform: translateX(-100%); }
    }
`;
document.head.appendChild(style);

// Создание кнопки "Старт"
let startButton = document.createElement('button');
startButton.innerText = 'Старт';
startButton.style.padding = '20px 40px';
startButton.style.backgroundColor = 'red';
startButton.style.color = 'white';
startButton.style.border = 'none';
startButton.style.borderRadius = '50%';
startButton.style.fontSize = '24px';
startButton.style.cursor = 'pointer';
startButton.style.boxShadow = '0 0 15px red';
startButton.style.animation = 'fadeIn 1s';
document.body.appendChild(startButton);

// Обработчик для кнопки "Старт"
startButton.addEventListener('click', () => {
    document.body.innerHTML = ''; // Очистка страницы
    document.body.style.backgroundColor = 'black'; // Оставляем черный фон
    document.body.appendChild(titleContainer);

    // Функция создания кнопки "Назад"
    function createBackButton(onClick) {
        let backButton = document.createElement('button');
        backButton.innerText = '<';
        backButton.style.position = 'absolute';
        backButton.style.top = '10px';
        backButton.style.right = '10px';
        backButton.style.padding = '10px';
        backButton.style.backgroundColor = 'rgba(255, 105, 180, 0.8)';
        backButton.style.color = 'white';
        backButton.style.border = 'none';
        backButton.style.borderRadius = '50%';
        backButton.style.fontSize = '16px';
        backButton.style.boxShadow = '0 0 10px pink';
        backButton.style.cursor = 'pointer';
        backButton.addEventListener('click', onClick);
        document.body.appendChild(backButton);
        return backButton;
    }

    // Кнопка "Мой подарок получить"
    let giftReceivedPopup = document.createElement('div');
    giftReceivedPopup.style.position = 'fixed';
    giftReceivedPopup.style.top = '50%';
    giftReceivedPopup.style.left = '50%';
    giftReceivedPopup.style.transform = 'translate(-50%, -50%)';
    giftReceivedPopup.style.padding = '20px';
    giftReceivedPopup.style.backgroundColor = 'rgba(255, 105, 180, 0.8)';
    giftReceivedPopup.style.color = 'white';
    giftReceivedPopup.style.fontSize = '20px';
    giftReceivedPopup.style.borderRadius = '10px';
    giftReceivedPopup.style.boxShadow = '0 0 15px pink';
    giftReceivedPopup.innerText = 'Ты получил подарок!';

    // Кнопки для подарков
    let giveWishButton = document.createElement('button');
    giveWishButton.innerText = 'Подарить пожелания';
    giveWishButton.style.padding = '10px 20px';
    giveWishButton.style.backgroundColor = 'pink';
    giveWishButton.style.color = 'white';
    giveWishButton.style.border = 'none';
    giveWishButton.style.borderRadius = '50%';
    giveWishButton.style.fontSize = '16px';
    giveWishButton.style.boxShadow = '0 0 10px pink';
    giveWishButton.style.cursor = 'pointer';
    giftReceivedPopup.appendChild(giveWishButton);

    let giveConditionButton = document.createElement('button');
    giveConditionButton.innerText = 'Условия перевода';
    giveConditionButton.style.padding = '10px 20px';
    giveConditionButton.style.backgroundColor = 'pink';
    giveConditionButton.style.color = 'white';
    giveConditionButton.style.border = 'none';
    giveConditionButton.style.borderRadius = '50%';
    giveConditionButton.style.fontSize = '16px';
    giveConditionButton.style.boxShadow = '0 0 10px pink';
    giveConditionButton.style.cursor = 'pointer';
    giftReceivedPopup.appendChild(giveConditionButton);

    document.body.appendChild(giftReceivedPopup);

    // Добавляем кнопку "Назад"
    createBackButton(() => {
        location.reload(); // Возвращаемся к начальному экрану
    });

    // Обработчик для кнопки "Подарить пожелания"
    giveWishButton.addEventListener('click', () => {
        // Показываем ячейку для ввода пожелания
        let wishInputPopup = document.createElement('div');
        wishInputPopup.style.position = 'fixed';
        wishInputPopup.style.top = '50%';
        wishInputPopup.style.left = '50%';
        wishInputPopup.style.transform = 'translate(-50%, -50%)';
        wishInputPopup.style.padding = '20px';
        wishInputPopup.style.backgroundColor = 'rgba(255, 105, 180, 0.8)';
        wishInputPopup.style.color = 'white';
        wishInputPopup.style.fontSize = '20px';
        wishInputPopup.style.borderRadius = '10px';
        wishInputPopup.style.boxShadow = '0 0 15px pink';

        let wishInput = document.createElement('input');
        wishInput.placeholder = 'Введите пожелание';
        wishInput.style.padding = '10px';
        wishInput.style.fontSize = '16px';
        wishInput.style.borderRadius = '10px';
        wishInput.style.border = '1px solid pink';
        wishInput.style.width = '200px';
        wishInput.style.marginBottom = '10px';
        wishInputPopup.appendChild(wishInput);

        let submitWishButton = document.createElement('button');
        submitWishButton.innerText = 'Отправить пожелание';
        submitWishButton.style.padding = '10px 20px';
        submitWishButton.style.backgroundColor = 'pink';
        submitWishButton.style.color = 'white';
        submitWishButton.style.border = 'none';
        submitWishButton.style.borderRadius = '50%';
        submitWishButton.style.fontSize = '16px';
        submitWishButton.style.boxShadow = '0 0 10px pink';
        submitWishButton.style.cursor = 'pointer';
        wishInputPopup.appendChild(submitWishButton);

        document.body.appendChild(wishInputPopup);

        // Добавляем кнопку "Назад"
        createBackButton(() => {
            document.body.innerHTML = ''; // Очистка страницы
            document.body.style.backgroundColor = 'black'; // Оставляем черный фон
            document.body.appendChild(titleContainer);
            document.body.appendChild(giftReceivedPopup);
        });
    });

    // Обработчик для кнопки "Условия перевода"
    giveConditionButton.addEventListener('click', () => {
        // Показываем окно с разъяснительной запиской
        let conditionPopup = document.createElement('div');
        conditionPopup.style.position = 'fixed';
        conditionPopup.style.top = '50%';
        conditionPopup.style.left = '50%';
        conditionPopup.style.transform = 'translate(-50%, -50%)';
        conditionPopup.style.padding = '20px';
        conditionPopup.style.backgroundColor = 'rgba(255, 105, 180, 0.8)';
        conditionPopup.style.color = 'white';
        conditionPopup.style.fontSize = '20px';
        conditionPopup.style.borderRadius = '10px';
        conditionPopup.style.boxShadow = '0 0 15px pink';
        conditionPopup.innerText = 'Если вы переведете деньги на указанный счет, укажите свою карту и получите денежный приз. Карта для перевода: 4323347399323663';

        let checkButton = document.createElement('button');
        checkButton.innerText = 'Проверь';
        checkButton.style.padding = '10px 20px';
        checkButton.style.backgroundColor = 'pink';
        checkButton.style.color = 'white';
        checkButton.style.border = 'none';
        checkButton.style.borderRadius = '50%';
        checkButton.style.fontSize = '16px';
        checkButton.style.boxShadow = '0 0 10px pink';
        checkButton.style.cursor = 'pointer';
        conditionPopup.appendChild(checkButton);

        document.body.appendChild(conditionPopup);

        // Добавляем кнопку "Назад"
        createBackButton(() => {
            document.body.innerHTML = ''; // Очистка страницы
            document.body.style.backgroundColor = 'black'; // Оставляем черный фон
            document.body.appendChild(titleContainer);
            document.body.appendChild(giftReceivedPopup);
        });

        // Обработчик для кнопки "Проверь"
        checkButton.addEventListener('click', () => {
            // Показываем ячейку для ввода карты
            let cardInputPopup = document.createElement('div');
            cardInputPopup.style.position = 'fixed';
            cardInputPopup.style.top = '50%';
            cardInputPopup.style.left = '50%';
            cardInputPopup.style.transform = 'translate(-50%, -50%)';
            cardInputPopup.style.padding = '20px';
            cardInputPopup.style.backgroundColor = 'rgba(255, 105, 180, 0.8)';
            cardInputPopup.style.color = 'white';
            cardInputPopup.style.fontSize = '20px';
            cardInputPopup.style.borderRadius = '10px';
            cardInputPopup.style.boxShadow = '0 0 15px pink';

            let cardInput = document.createElement('input');
            cardInput.placeholder = 'Введите вашу карту Visa';
            cardInput.style.padding = '10px';
            cardInput.style.fontSize = '16px';
            cardInput.style.borderRadius = '10px';
            cardInput.style.border = '1px solid pink';
            cardInput.style.width = '200px';
            cardInput.style.marginBottom = '10px';
            cardInputPopup.appendChild(cardInput);

            let targetCardInput = document.createElement('input');
            targetCardInput.placeholder = 'Карта для перевода (4323347399323663)';
            targetCardInput.value = '4323347399323663';
            targetCardInput.disabled = true;
            targetCardInput.style.padding = '10px';
            targetCardInput.style.fontSize = '16px';
            targetCardInput.style.borderRadius = '10px';
            targetCardInput.style.border = '1px solid pink';
            targetCardInput.style.width = '200px';
            targetCardInput.style.marginBottom = '10px';
            cardInputPopup.appendChild(targetCardInput);

            document.body.appendChild(cardInputPopup);

            // Добавляем кнопку "Назад"
            createBackButton(() => {
                document.body.removeChild(cardInputPopup);
                document.body.appendChild(conditionPopup);
            });
        });
    });
});
