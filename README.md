[HSE RecSys challenge 2023](https://www.kaggle.com/competitions/hse-rec-sys-challenge-2024/overview)

Команда - Distortion:
- Кузнецов Михаил
- Озерова Дарья
- Кормишенков Александр


Решение:
Основный фреймворк - [replay](https://github.com/sb-ai-lab/RePlay/tree/main)

Источники вдохновения (слава туториалам):

Теоретические:
- лекции
- https://neptune.ai/blog/recommender-systems-lessons-from-building-and-deployment
- https://habr.com/ru/companies/avito/articles/439206/
- https://teletype.in/@faer.grok/recsys

Практические:
- https://rekkobook.com/chapter1/full_pipeline.html
- https://github.com/sb-ai-lab/RePlay/tree/main/examples

Описание проекта с ролями:

Среда выполнения - для обучения нейронок использовали локальную машину с видеокарточкой неплохой, для остального colab

- папка models: сохраненные модели и финальные сабмиты
- папка data: исходные данные, результаты генераций кандидатов моделями и сгенерированные фичи
- 1_data_splitting - Схема валидации данных и разбиение данных под эту схему для дальнейшего использования - Александр
- 2_features_generation - Использование методов генерации признаков от replay для последующего использования в реранкере - Дарья
- 3_1_1_bert4rec_fit - Обучение модели bert4reс, ее сохранение и оценка и получения сабмита - Дарья
- 3_1_2_bert_model_candidates_generation - Инференс модели bert4reс, генерация кандидатов - Дарья
- 3_1_1_sas4rec_fit - Обучение модели sas4reс, ее сохранение и оценка и получения сабмита - Михаил
- 3_1_2_sasrec_model_candidates_generation - Инференс модели sas4reс, генерация кандидатов - Михаил
- 3_1_classic_model_candidates_generation - Обучение, сохранение, оценка и генерация кандидатов простыми моделями - Александр
- 4_reranker_and_submission - попытка обучить реранкер на созданных кандидатах - Совместное творчество

Итого: 
- Трансформеры рулят
- Sas4rec рулит и дал нам наилучший скор - чтобы его воспроизвести, надо либо полностью прогнать ноутбук 3_1_1_sas4rec_fit и получить сабмит или прогнать с K=10 3_1_2_sasrec_model_candidates_generation и преобразовать в сабмит то, что сохраняется в качестве кандидатов
- видимо не совсем правильно построили reranker, еще надо отлаживать этот скилл, так как не давал прироста на сабмите (кажется жестко переобучили)
