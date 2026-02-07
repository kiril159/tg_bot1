<!DOCTYPE html>
<html>
<head>
    <title>Connecting...</title>
    <meta charset="UTF-8">
    <!-- Подключаем официальный скрипт Telegram -->
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
</head>
<body>
    <script>
        // Инициализируем Web App API
        const tg = window.Telegram.WebApp;

        // Функция для отправки данных боту
        function connect() {
            // tg.initDataUnsafe.start_param содержит значение из ?startapp=...
            const scannedUserId = tg.initDataUnsafe.start_param;

            if (scannedUserId) {
                // Формируем текст сообщения, которое получит бот
                const message = `connect_${scannedUserId}`;
                
                // Отправляем данные боту. Он получит это как обычное сообщение в чате.
                tg.sendData(message);

            } else {
                // Если параметр не найден (маловероятно), просто закрываем
                tg.close();
            }
        }

        // Ждем, пока API будет готово
        tg.ready();
        
        // Вызываем нашу функцию
        connect();
    </script>
</body>
</html>
