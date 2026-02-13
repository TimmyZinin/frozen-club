# Архитектура воронок Frozen Club

## Общая схема

```mermaid
graph TB
    subgraph "ПРИВЛЕЧЕНИЕ"
        A1[Реклама VK/Max] --> Q[Квиз]
        A2[Контент TG/VK] --> LP[Лендинг клуба]
        A3[Вебинар] --> LP
        A4[Бесплатный урок] --> LP
        A5[Мини-курс 5 дней] --> LP
    end

    subgraph "КОНВЕРСИЯ"
        Q --> |email| WS[Welcome-серия 5 писем]
        LP --> |прямая| TR[Trial 7 дней]
        LP --> |оплата| PAY[Оплата Prodamus]
        WS --> NS[Nurture-серия 7 писем]
        NS --> SS[Sales-серия 5 писем]
        SS --> TR
        SS --> PAY
    end

    subgraph "АКТИВАЦИЯ"
        TR --> |конвертировался| OS[Onboarding 5 писем]
        PAY --> OS
        TR --> |не конвертировался| RS[Reactivation 3 письма]
    end

    subgraph "УДЕРЖАНИЕ"
        OS --> RET[Retention-серия]
        RET --> |30 дней| UP[Upsell Базовый→Про]
        RET --> |перед продлением| REN[Renewal-серия]
        REN --> |не продлил| RS
    end

    style TR fill:#2D5A3D,color:#fff
    style PAY fill:#C28A5A,color:#fff
    style RS fill:#E53935,color:#fff
```

## 5 воронок

| # | Воронка | Аудитория | Цель | Конверсия (цель) |
|---|---------|-----------|------|-----------------|
| 1 | Холодный трафик | Новые люди | Email → Trial | 3-5% в подписку |
| 2 | Тёплый трафик | 10 000+ учениц | Прямая подписка | 5-10% |
| 3 | Вебинарная | Регистранты вебинара | Подписка после вебинара | 10-15% |
| 4 | Пробный доступ | Все посетители лендинга | Trial → Paid | 30%+ |
| 5 | Upsell | Базовые подписчицы | Базовый → Профессионал | 15-20% |

## Триггеры переходов между воронками

```mermaid
graph LR
    REG[Регистрация email] --> |День 0| W1[Welcome Email 1]
    W1 --> |День 1| W2[Welcome Email 2]
    W2 --> |День 3| W3[Welcome Email 3]
    W3 --> |День 5| W4[Welcome Email 4]
    W4 --> |День 7| W5[Welcome Email 5]

    W5 --> |не купил| N1[Nurture Email 1]
    W5 --> |купил| O1[Onboarding Email 1]

    N1 --> |каждые 3-4 дня| N7[Nurture 7 писем]
    N7 --> |не купил| S1[Sales Email 1]
    N7 --> |купил| O1

    S1 --> |5 дней| S5[Sales 5 писем]
    S5 --> |не купил| COLD[Перевод в cold list]
    S5 --> |купил| O1

    style O1 fill:#2D5A3D,color:#fff
    style COLD fill:#999,color:#fff
```

## Метрики по воронкам

### Основные KPI

| Этап | Метрика | Цель |
|------|---------|------|
| Привлечение | CPL (Cost Per Lead) | < 150 ₽ |
| Привлечение | CTR рекламы | > 1.5% |
| Конверсия | Email open rate | > 35% |
| Конверсия | Email click rate | > 5% |
| Конверсия | Landing → Trial | > 15% |
| Конверсия | Trial → Paid | > 30% |
| Активация | Onboarding completion | > 60% |
| Удержание | Monthly churn | < 8% |
| Upsell | Basic → Pro upgrade | > 15% |

### Точки отслеживания

1. **Вход в воронку:** источник трафика (VK ads, organic TG, webinar, referral)
2. **Регистрация email:** форма на лендинге или квизе
3. **Welcome-серия:** open rate, click rate каждого письма
4. **Trial start:** дата начала, источник
5. **Trial активность:** сколько уроков посмотрел за 7 дней
6. **Оплата:** тариф, способ оплаты, рассрочка
7. **Onboarding:** % завершения серии, первый урок, первое сообщение в чате
8. **Retention:** активность в неделю/месяц, прогресс по курсам
9. **Churn:** дата отмены, причина (если указана)
