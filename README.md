# Курсовой проект по предмету Информационные системы и базы данных

### Предметная область "Вселенная анимационного сериала Наруто"

Существует мир ниндзя. В нём живут ниндзя и обычные люди. Мир разделён на страны, охраняемые деревнями (скрытыми селениями). Каждая страна охраняется одной и только одной деревней. Ниндзя живут в деревнях. Один ниндзя может жить только в одной деревне. Ниндзя принадлежит клану. Ниндзя может принадлежать только одному клану. Если родители из разных кланов выбирается более престижный. Бидзю это древние животные ниндзя. Деревня может захватить бидзю и запечатать его в одном из ниндзя, этот ниндзя становится Джинчурики. Бидзю различаются количеством хвостов, от одного до десяти, чем больше хвостов, тем он сильнее. Семьи ниндзя, проживающие в скрытых деревнях, отдают своих детей в академию ниндзя в малом возрасте и детям назначается ранг ученик академии. Каждый ниндзя в период службы зарабатывает ранги: ученик академии/генин/чунин/джонин/анбу/каге. Получение второго и третего рангов сопровождается экзаменом, по его итогам решается, перешел ли ниндзя на следующую ступень. Ниндзя используют техники. Техники могут быть запретными, могут быть особенностью клана, могут быть стихийными. Техники особенностей клана используют только наследники клана. Ниндзя участвуют в сражениях и войнах. Сражения происходят на территориях разных стран, рождают героев и получают жертвы. Если во время войны был убит глава деревни (Каге), по итогам войны выбирается новый из числа героев. В войнах также есть противоборствующие стороны, но также войны являются совокупностью битв.

### Модель базы данных 
![модель базы данных](https://github.com/Avvessalom/ITMO-Information-Systems-and-Databases-Course-Project/blob/main/img/KP.jpg)
### Сценарии использования базы данных
Основное предназначение базы данных, это сохранение данных о мире ниндзя, сохранение истории и техник.

Из предназначения базы данных следуют основные пути её использования:
* Добавление нового(новой):
    * ниндзя;
    * гражданина;
    * техники;
    * клана;
    * войны;
    * битвы.
* Разрушение скрытой деревни ниндзя;
* Восстановление разрушенной деревни ниндзя;
* Смена джинчурики;

#### Описание основных прецедентов
Прецедент             | Добавление нового ниндзя 
:-----:               | :---- 
ID                    | 1 
Краткое описание      | В таблицу `Ninja` добавляется новый ниндзя
Главные акторы        | Администратор базы данных, историк ниндзя
Второстепенные акторы | нет
Предусловия           | О ниндзя должна быть обязательно заполнена следующая информация: имя, клан, возраст, пол, деревня, а также должно быть известно мертв он или жив. Клан и деревня к которым привязан ниндзя должны существовать.
Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вносят информацию о ниндзя: `name`, `clan`, `village`, `age`, `sex`, `status`</li><li>Создается ниндзя с `name`, `clan`, `village`, `age`, `sex`, `status`</li></ol>    

Прецедент             | Добавление нового гражданина 
:-----                | :----
ID                    | 2 
Краткое описание      | В таблицу `Citizen` добавляется новый гражданин
Главные акторы        | Администратор базы данных, историк ниндзя
Второстепенные акторы | нет
Предусловия           | О гражданине должна быть обязательно заполнена следующая информация: имя, возраст, пол, деревня, а также должно быть известно мертв он или жив. Деревня к которой привязан гражданин должна существовать.
Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вносят информацию о гражданине: `name`, `village`, `age`, `sex`, `status`</li><li>Создается гражданин с `name`, `village`, `age`, `sex`, `status`</li></ol>    


Прецедент             | Добавление новой техники 
:-----                | :---- 
ID                    | 3 
Краткое описание      | В таблицу `Technic` добавляется новая техника
Главные акторы        | Администратор базы данных, историк ниндзя
Второстепенные акторы | нет
Предусловия           | О технике обязательно должна быть заполнена следующая информация: тип, дополнительный тип, является ли техника "ограничением крови", элемент техники, ранг, последовательность печатей для использования, имя. Тип, дополнительный тип и ранг техники должны существовать. Если техника является "ограничением крови", то клан использующий эту технику должен существовать.
Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вносят информацию о технике: `type`, `additional_type`, `blood_restriction`, `element`, `rank`, `rune seals`, `name`</li><li>Создается техника с `type`, `additional_type`, `blood_restriction`, `element`, `rank`, `rune seals`, `name`</li></ol>    


Прецедент             | Добавление нового клана 
:-----                | :----
ID                    | 4 
Краткое описание      | В таблицу `Clan` добавляется новый клан
Главные акторы        | Администратор базы данных, историк ниндзя
Второстепенные акторы | нет
Предусловия           | О клане обязательно должна быть заполнена следующая информация: название, деревня к которой этот клан привязан, престижность клана. Деревня должна существовать.
Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вносят информацию о клане: `name`, `village`, `prestige`</li><li>Создается клан с `name`, `village`, `prestige`</li></ol>    
 
 
 Прецедент             | Добавление новой войны 
 :-----                | :----
 ID                    | 5 
 Краткое описание      | В таблицу `War` добавляется новая война
 Главные акторы        | Администратор базы данных, историк ниндзя
 Второстепенные акторы | нет
 Предусловия           | О войне обязательно должна быть заполнена следующая информация: название, атакующая страна, защищающаяся страна, потери атакующих, потери обороняющихся, дата начала войны. Атакующая и обороняющаяся страны должны существовать.
 Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вносят информацию о войне: `name`, `attacking_country`, `defending_country`, `loss_of_attackers`, `loss_of_defenders`, `start_date`. Если война уже закончилась, то также вносится `end date` </li><li>Создаётся война с `name`, `attacking_country`, `defending_country`, `loss_of_attackers`, `loss_of_defenders`, `start_date`. Если была указана `end_date` то и с ней тоже</li></ol>
 
 Прецедент              | Добавление новой битвы 
  :-----                | :----
  ID                    | 6 
  Краткое описание      | В таблицу `Battle` добавляется новая битва
  Главные акторы        | Администратор базы данных, историк ниндзя
  Второстепенные акторы | нет
  Предусловия           | О битве обязательно должна быть заполнена следующая информация: война во время которой прошла эта битва, на территории какой страны прошла, потери, продолжительность, название, дата. Война и страна на территории которой прошла битва должны существовать. 
  Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вносят информацию о битве: `war`, `territory`, `loss`, `durration`, `name`, `date_of_battle`</li><li> Создаётся битва с `war`, `territory`, `loss`, `durration`, `name`, `date_of_battle`</li></ol>
  
  Прецедент              | Разрушение скрытой деревни ниндзя 
   :-----                | :----
   ID                    | 7 
   Краткое описание      | Существующая скрытая деревня ниндзя разрушается
   Главные акторы        | Администратор базы данных, историк ниндзя
   Второстепенные акторы | нет
   Предусловия           | Деревня должна существовать. Известно, что деревня была разрушена.
   Основной поток        | <ol><li>Администратор базы данных или историк ниндзя удаляют выбранную деревню;</li><li>Подсчитывается количество разрушений этой деревни</li><li>Информация о деревне и количестве её разрушений помещаются в таблицу `Destroyed_village`</li><li>В таблицу `Hidden_village` помещаются руины</li></ol>
   
   Прецедент             | Добавление пары Родитель_Ребенок
   :-----                | :----
   ID                    | 8 
   Краткое описание      | В таблицу `Parents` добавляется родитель и ребенок
   Главные акторы        | Администратор базы данных, историк ниндзя
   Второстепенные акторы | нет
   Предусловия           | Родитель и ребенок должны существовать.
   Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вносят в таблицу `Parents` пару Родитель_Ребенок</li><li>Проверяется уже существующее количество родителей у этого ребенка</li><li>Если родителей больше одного, то выводится исключение, запрещающее ребенку иметь более двух родителей</li><li>Если родитель один, то проверяется не совпадает ли, уже имеющийся родитель с новодобавленным</li><li>Если совпадает, то выводится исключение, запрещающее добавлять одного родителя дважды для одного ребенка</li><li>Если родителей нет, то пара добавляется</li></ol>
    
   Прецедент             | Проверка пары Ниндзя_Клан 
   :-----                | :----
   ID                    | 9 
   Краткое описание      | Проверка, находится ли ниндзя в указанном клане
   Главные акторы        | Администратор базы данных, историк ниндзя
   Второстепенные акторы | нет
   Предусловия           | Должна быть заполнена следующая информация: уникальный идентификатор ниндзя, уникальный идентификатор клана. Ниндзя и клан должны существовать.
   Основной поток        | <ol<li>Администратор базы данных или историк ниндзя вводят информацию об клане и ниндзя</li>><li>Проверяется присутствует ли указанный ниндзя в указанном клане</li></ol>
    
   Прецедент             | Определение клана ребенка 
   :-----                | :----
   ID                    | 10 
   Краткое описание      | При рождении ребенка от родителей из разных кланов, выбирается более престижный
   Главные акторы        | Администратор базы данных, историк ниндзя
   Второстепенные акторы | нет
   Предусловия           | Обязательно должна быть заполнена следующая информация: уникальный идентификатор ребенка. У ребенка должно быть два родителя, кланы родителей должны существовать.
   Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вводят информацию о ребенке</li><li>Выбираются родители этого ребенка</li><li>Выбираются кланы родителей</li><li>Вычисляется, клан какого из родителей престижнее</li><li>В таблицу `Ninja`, в поле `clan` вносятся изменения.</li></ol>
    
   Прецедент             | Запечатывание Бидзю 
   :-----                | :----
   ID                    | 11 
   Краткое описание      | Обновляется информация о Бидзю и его джинчурики(старом и новом) 
   Главные акторы        | Администратор базы данных, историк ниндзя
   Второстепенные акторы | нет
   Предусловия           | Обязательно должна быть заполнена следующая информация: уникальный идентификатор бидзю, уникальный идентификатор нового джинчурики. Бидзю и джинчурики должны существовать.
   Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вводят информацию о запечатываемом бидзю и о его новом джинчурики</li><li>Выбирается старый джинчурики</li><li>Статус старого джинчурики изменяется на `dead`</li><li>В таблицу `jinchuriki` добавляется новая пара Бидзю_Джинчурики</li></ol>
    
   Прецедент             | Выбор кандидатов на должность Каге  
   :-----                | :----
   ID                    | 12 
   Краткое описание      | Выбираются достойные кандидаты, которые могут занимать должность Каге. 
   Главные акторы        | Администратор базы данных, историк ниндзя
   Второстепенные акторы | нет
   Предусловия           | Обязательно должна быть заполнена следующая информация: уникальный идентификатор старого Каге, война в которой он погиб.
   Основной поток        | <ol><li>Администратор базы данных или историк ниндзя вводят информацию о Каге и его смерти</li><li>Выбирается деревня погибшего каге</li><li>Выбираются герои войны, в которой погиб Каге и из них выбираются жители деревни погибшего Каге</li><li>Выводятся кандидаты на пост Каге</li></ol>
    
   Прецедент             | Добавление нового 
   :-----                | :----
   ID                    | 13 
   Краткое описание      | В таблицу 
   Главные акторы        | Администратор базы данных, историк ниндзя
   Второстепенные акторы | нет
   Предусловия           | Обязательно должна быть заполнена следующая информация
   Основной поток        | <ol><li></li><li></li></ol>
    
    
### Функции:
* `clan_selection_for_a_child` - функция позволяет определять принадлежность новорожденного ниндзя к клану;
* `seal_the_biju` - функция позволяет осуществлять смену Джинчурики;
* `choose_kage_candidates` - функция позволяет показать кандидатов на должность нового Каге в случае смерти предыдущего;
* `check_clan` - простая вспомогательная функция, возвращающая присутствует проверяемый ниндзя в проверяемом клане или нет
### Триггеры:
* `on_destroy` - триггер срабатывающий при взаимодействии с `destroyed_village` и добавляющий руины на место уничтоженной деревни;  
* `on_jinchuriki_die` - триггер запрещающий удаление Джинчурики;
* `on_actions_with_village` - триггер срабатывающий при удалении деревни из `hidden_village` и  автоматически вносящий изменения в `destroyed_village`; 
* `on_death` - триггер срабатывающий при смерти ниндзя и проверяющий был ли он Каге. В случае если это так начинается подбор кандидатов на его место.
* `check_blood_restriction` - триггер срабатывающий каждый раз, когда к ниндзя добавляется новая техника. Триггер проверяет, является ли техника особенностью клана. И если является, то может ли этот ниндзя её использовать. 
* `check_clan_leader` - триггер срабатывающий при обновлении лидеров клана. Проверяет, присутствует ли претендент в клане и жив ли он
* `check_parents` - триггер срабатывающий при добавлении пары `Родитель_Ребенок` и проверяющий не является ли родитель этого ребенка дважды его родителем. Также проверяется количество родителей, не больше двух.
### Индексы:
* `ninjaid` - hash индекс на атрибут `ninja_id` таблицы `Ninja`, необходим в следствии частого 
* `countryid` - 
* `clan_name` - составной b-tree индекс на атрибуты `clan_id` и `name` таблицы `Clan` необходим для 