
@startuml
left to right direction
skinparam packageStyle rectangle

actor "Користувач" as User
actor "Покупець" as Customer
actor "Адміністратор" as Admin
actor "Платіжний сервіс" as PaymentService

User <|-- Customer
User <|-- Admin

rectangle "Онлайн-магазин" {
  usecase "Переглянути каталог" as UC01
  usecase "Переглянути товар" as UC02
  usecase "Оформити замовлення" as UC03
  usecase "Перевірити кількість" as UC04
  usecase "Зафіксувати ціну" as UC05
  usecase "Оплатити замовлення" as UC06
  usecase "Передати платіж" as UC07
  usecase "Зберегти результат оплати" as UC08
  usecase "Додати товар" as UC09
  usecase "Оновити статус замовлення" as UC10
  usecase "Показати помилку кількості" as UC11
}

User --> UC01
User --> UC02
Customer --> UC03
Customer --> UC06
Admin --> UC09
Admin --> UC10
PaymentService --> UC08

UC03 ..> UC04 : <<include>>
UC03 ..> UC05 : <<include>>
UC06 ..> UC07 : <<include>>
UC06 ..> UC08 : <<include>>
UC11 ..> UC03 : <<extend>>

@enduml
