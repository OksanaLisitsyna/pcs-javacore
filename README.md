## Дипломная работа. Менеджер задач

В этом задании разрабатывался сервер, отвечающий за менеджмент списка дел. 
</br></br>
Каждая задача представляет собой значение типа *String*. Класс *Todos* хранит эти задачи в *TreeSet\<String\>*.
TreeSet был использован, т.к. этот класс сам контролирует уникальность элементов и сортирует их. Это позволяет сильно ускорить работу сервера, если задач для сортировки много, и экономит память, избегая хранения дубликатов.</br></br>
Менеджер задач принимает запросы на добавление или удаление задач через сервер *TodoServer*.  После старта, он в бесконечном цикле принимает подключения и считывает с них одну строку, в которой располагается json вида:
```json
{ "type": "ADD", "task": "Название задачи" }
```
где `type` - тип операции (ADD или REMOVE), а `task` - сама задача.
Т.е., одна операция соответствует одному запросу.
</br>Для парсинга входных данных использовалась библиотекой **GSon** от Google. </br></br>
В ответ на запрос сервер присылает клиенту статус выполнения команды и текущее состояние списка задач.
</br></br>
*Клиент*, созданный для демонстрации, генерирует задачу со случайным именем и отправляет ее на сервер (для этого используются средства стандартных пакетов **java.io** и **java.net**: Socket, BufferedReader, PrintWriter).
