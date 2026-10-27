flowchart TD
    Start([Клиент прибывает по геометке]) --> LookForSign[Ищет глазами вывеску]
    LookForSign --> IsSignVisible{Вывеска видна?}
    
    IsSignVisible -- Нет --> Wander[Плутает, проходит мимо двери]
    Wander --> AskStaff[Заходит и жалуется: «Где вывеска?»]
    
    IsSignVisible -- Да --> Enter[Заходит в ПВЗ]
    AskStaff --> Enter
    
    Enter --> GetOrder[Сотрудник выдает заказ]
    GetOrder --> End([Клиент получил заказ])

    Wander -. Решение To-Be .-> CheckApp[Клиент открывает приложение]
    CheckApp --> SeePhoto[Смотрит фото-ориентиры]
    SeePhoto --> FindDoor[Находит нужную дверь]
    FindDoor --> Enter

    classDef problem fill:#ffe6e6,stroke:#cc0000,stroke-width:1px;
    class Wander,AskStaff problem;
