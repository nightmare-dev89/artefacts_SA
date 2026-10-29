Задокументируйте все варианты использования, связанные с просмотром списка брендов, созданием, изменением и удалением бренда при помощи Use Case Diagram в соответствии с бизнес-требованиями.

**Бизнес-требования**
В рамках функционирования маркетплейса планируется создание отдельной страницы, предназначенной для товаров категории «одежда». Этот функциональный блок будет предоставлять пользователям возможность осуществлять поиск, просмотр брендов списком, выбирать бренды(переходить на товары) из предложенного списка и сортировать их в алфавитном порядке.

В то же время данный функциональный блок будет передан на поддержку контент-менеджерам, которые будут иметь возможность посмотреть бренды списком, а также смогут создавать, изменять и удалять бренды. При создании или изменении бренда необходимо будет привязывать к нему коллекцию товаров. Каждый бренд будет иметь своё уникальное название и логотип.

@startuml
left to right direction

actor Пользователь as User
actor "Контент менеджер" as Manager

(Блок клиента) as (clientContent)
(Просмотр\nбрендов\nсписком) as (viewBrend)
(Поиск\nбренда) as (brandSearch)
(Выбор\nбренда) as (selectBrands)
(Переход\nк товарам) as (goProduct)

(Блок менеджера) as (managerContent)
(Просмотр\nбрендов\nсписком) as (viewBrends)
(Создание\nбренда) as (createBrand)
(Изменение\nбренда) as (rebranding)
(Удаление \nбренда) as (deleteBrand)
(Привязка\nколлекции товаров\nс уникальным названием\nи лого) as (linkProduct) 

User -- clientContent

clientContent -.> brandSearch: <<include>>
clientContent -.> viewBrend: <<include>>
viewBrend -.> selectBrands: <<include>>
brandSearch -.> selectBrands: <<include>>
selectBrands -.> goProduct: <<include>>

Manager -- managerContent

managerContent -.> viewBrends: <<include>>
viewBrends -.> createBrand: <<include>>
createBrand -.> linkProduct: <<extend>>
viewBrends -.> rebranding: <<include>>
rebranding -.> linkProduct: <<extend>>
viewBrends -.> deleteBrand: <<include>>

@enduml
