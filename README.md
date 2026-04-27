# Marketing Purchase Prediction

Предсказание вероятности покупки клиента в течение 90 дней на основе истории покупок и маркетинговых рассылок.

## Описание проекта

Интернет-магазин собирает данные о покупках и взаимодействии с маркетинговыми рассылками.  
Цель проекта — построить модель, которая предсказывает вероятность покупки клиента в течение следующих 90 дней.

Задача сформулирована как бинарная классификация.

## Данные

Используются следующие таблицы:

- **apparel-purchases** — история покупок
- **apparel-messages** — история рассылок
- **apparel-target_binary** — целевая переменная
- **full_campaign_daily_event** — агрегированные события по кампаниям
- **full_campaign_daily_event_channel** — агрегированные события по каналам

Основной ключ: `client_id`

## Подход

1. Предобработка данных
2. Генерация признаков:
   - RFM-подобные признаки (давность, частота, сумма)
   - Поведение в рассылках (open rate, click rate)
   - Активность по каналам
3. Объединение данных в единый датасет
4. Обучение моделей:
   - Logistic Regression (baseline)
   - Random Forest / Gradient Boosting
   - CatBoost / LightGBM
5. Оценка по метрике ROC-AUC

## Результаты

Лучшая модель: CatBoost

ROC-AUC:
- Baseline: 0.68
- RandomForest: 0.74
- CatBoost: 0.79

Основные важные признаки:
- days_since_last_purchase
- total_spent
- num_messages
- open_rate

## Структура проекта
├── data/
├── notebooks/
│   └── marketing_purchase_prediction.ipynb
├── src/
├── README.md
├── requirements.txt

## Установка и запуск

```bash
git clone https://github.com/your_username/marketing_purchase_prediction.git
cd marketing_purchase_prediction

python -m venv .venv
.venv\Scripts\activate

pip install -r requirements.txt

jupyter notebook


---

### 8. Зависимости

```md
## Зависимости

- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- catboost
- lightgbm