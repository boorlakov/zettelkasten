# Файловые системы

[<- Назад (конспекты по осям)](https://github.com/boorlakov/zettelkasten/blob/main/university/operation%20systems%20and%20IDE/README.md)

## Внешняя память делится на

- ### Устройство внешней памяти

- ### Физический носитель, то есть то, что хранится, например

  - Магнитные диски (**HDD**)
  - Оптические диски (диски прямо как в детстве)
  - Магнитооптические диски
  - Твердотельные накопители (**SSD**)
  - USB флэшки
  - Карты памяти
- Файловая система
- Способ хранения данных с физического носителя

## Физическая модель диска

- ### На хардварьном уровне работа происходит через контроллер, знает

  - Физические параметры устройства
  - Для дисков например информации располагают вдоль концентрических окружностей (**tracks**)
  - Треки с одинаковыми номерами на разных поверхностях образуют цилиндр
  
- ### Для чтения-записи выделяют отдельную магнитную головку

  - **Трек**

    - Количество секторов, участков дорожки, хранящие минимальную порцию информации (**512 байт**)

    - Нумеруется в пределах поверхности
    - Возможность разбить трек на сектора
      - На константное количество, т.к. обеспечивается изменением плотности записи при переходе с дорожки. Для обращения нужно знать физический адрес
      - На переменное количество
