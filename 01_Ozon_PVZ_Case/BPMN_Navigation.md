# Процесс навигации клиента (BPMN)

Ниже представлен процесс пути клиента от прибытия по адресу до получения заказа. Диаграмма показывает проблему (As-Is) и предлагаемое решение (To-Be).

```mermaid
flowchart TD
    %% Начало
    Start((Клиент прибыл по геометке)) --> SearchSign[Ищет вывеску над входом]
    
    %% Развилка
    SearchSign --> CheckSign{Вывеска видна?}
    
    %% Ветка проблем (As-Is)
    CheckSign -- Нет (As-Is) --> Confused[Плутает, проходит мимо двери]
    Confused --> Angry[Приходит злой, жалуется сотруднику]
    
    %% Ветка решения (To-Be)
    Confused -. Решение To-Be .-> CheckApp[Клиент открывает приложение/карты]
    CheckApp --> LookPhoto[Смотрит фото-ориентиры и описание маршрута]
    LookPhoto --> FindDoor[Находит нужную дверь]
    
    %% Успешный сценарий
    CheckSign -- Да --> EnterPVZ[Заходит в ПВЗ]
    FindDoor --> EnterPVZ
    
    %% Завершение
    EnterPVZ --> GetOrder[Сотрудник выдает заказ]
    Angry -. Жалоба обработана .-> GetOrder
    GetOrder --> End((Клиент получил заказ))

    %% Стили (опционально)
    classDef problem fill:#ffcccc,stroke:#ff0000,stroke-width:2px;
    classDef solution fill:#ccffcc,stroke:#00ff00,stroke-width:2px;
    class Confused,Angry problem;
    class CheckApp,LookPhoto,FindDoor solution;
