1 шаг. Зайдем в Cloud Run на Google Cloud Platform и нажмем на Deploy.

![telegram-cloud-photo-size-2-5206196087780668060-y](https://github.com/user-attachments/assets/0ce9c617-a136-44cc-9054-d31d95776500)

2 шаг. Используем существующий сервис hello и выставим минимальные настройки сервиса. Установим 8080 порт. Дадим доступ неавторизованным пользователям.

![telegram-cloud-photo-size-2-5206196087780668062-y](https://github.com/user-attachments/assets/6ff450c2-6a5d-4471-b5fc-d614cd61b02a)

![telegram-cloud-photo-size-2-5206196087780668063-y](https://github.com/user-attachments/assets/68a1e3e2-ceb8-40b9-9a97-98ba2cbb72ab)


3 шаг. Проверим, что сервис запущен.

![telegram-cloud-photo-size-2-5206196087780668070-y](https://github.com/user-attachments/assets/b00d31b2-b03e-4ef5-833c-61b70ef966eb)

4 шаг. По ссылке проверим работоспособность сервиса, удостоверяемся, что все сработало.

![telegram-cloud-photo-size-2-5206196087780668072-y](https://github.com/user-attachments/assets/224e7bc1-62c4-4dce-a23b-dc3e4e9589ab)

5 шаг. Просмотрим текущие Logs и Metrics.

![telegram-cloud-photo-size-2-5206196087780668120-y](https://github.com/user-attachments/assets/31910356-8996-4809-ad6b-7cc9e707d2ac)

![telegram-cloud-photo-size-2-5206196087780668124-y](https://github.com/user-attachments/assets/d46bd4cc-56e1-4396-9cd9-3ba3f68f9182)

6 шаг. Выставим для данного Cloud Run 8090 порт и применим трафик на 50%.

![telegram-cloud-photo-size-2-5206196087780668129-y](https://github.com/user-attachments/assets/a895650a-37db-43ea-a1ee-d17644ab1008)

7 шаг. Рассмотрим изменения в метриках и при логах при изменении трафика и порта. 

- В логах видно, что контейнер теперь запускается и слушает порт 8090 вместо 8080.
- Произошло обновление сервиса (ReplaceService), после чего контейнер выводит сообщение о старте на новом порту.
- Container Instance Count: наблюдался всплеск до двух активных экземпляров во время переключения.
- CPU/Memory Utilization: минимальные нагрузки, стабильные показатели (CPU около 1%, память около 10-20%).
- Container Startup Latency: небольшая задержка старта контейнера (примерно 80 мс).
- Max Concurrent Requests: максимум 2 одновременных запроса во время переключения.

![telegram-cloud-photo-size-2-5206196087780668132-y](https://github.com/user-attachments/assets/eb90bdb5-6a1f-4438-b47c-d198ef3c2cf4)

![telegram-cloud-photo-size-2-5206196087780668153-y](https://github.com/user-attachments/assets/ba70a9d4-d113-4a4c-a924-71574b07f8cf)

![telegram-cloud-photo-size-2-5206196087780668154-y](https://github.com/user-attachments/assets/9944c6ef-5c4c-4590-a090-9204b4d8295c)

![telegram-cloud-photo-size-2-5206196087780668155-y](https://github.com/user-attachments/assets/d32b2286-8a2a-48b3-9cf1-5e658eba67ce)

8 шаг. Удалим Cloud Run.
