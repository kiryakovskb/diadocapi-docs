﻿DocumentWorkflow
================

Представляет вид документооборота для функции документа :ref:`DocumentFunction <document-function>`.

.. code-block:: protobuf

    message DocumentWorkflow {
        required int32 Id = 1;
        required bool IsDefault = 2;
    }

-  *Id* - уникальный числовой идентификатор вида документооборота
-  *IsDefault* - вид документооборота будет использован по умолчанию

.. csv-table:: Виды документооборота
    :header: "Id", "Вид", "Ответное действие", "Подтверждение оператора", "Используется как приглашение", "Извещение о получении титула отправителя", "Извещение о получении титула получателя"
    :widths: 10, 10, 10, 10, 10, 10, 10

    "1", "Двусторонний", "Подпись (по запросу)", "Нет", "Нет", "По запросу", "Нет"
    "2", "Двусторонний", "Подпись", "Нет", "Нет", "По запросу", "Нет"
    "3", "Двусторонний", "Титул", "Нет", "Нет", "По запросу", "Нет"
    "4", "Односторонний", "—", "Да", "Нет", "Обязательно", "Нет"
    "5", "Двусторонний", "Титул", "Да", "Нет", "Обязательно", "Нет"
    "6", "Односторонний", "—", "Нет", "Нет", "По запросу", "Нет"
    "7", "Приглашение к ЭДО", "Подпись (по запросу)", "Нет", "Да", "Нет", "Нет"
    "8", "Двусторонний", "Титул", "Нет", "По запросу", "Нет", "Нет"
    "9", "Односторонний", "—", "Нет", "Нет", "По запросу", "Нет"
    "10", "Односторонний", "—", "Да", "Нет", "Обязательно", "Нет"
    "11", "Двусторонний", "Титул", "Нет", "Нет", "По запросу", "По запросу"
    
- *Подпись (по запросу)* - это значит, что в структуре :doc:`DocumentAttachment` установлено поле `NeedRecipientSignature`
- *Извещение о получении титула отправителя по запросу* - это значит, что в структуре :doc:`DocumentAttachment` установлено поле `NeedReceipt`
- *Извещение о получении титула получателя по запросу* - это значит, что в структуре :doc:`RecipientTitleAttachment <MessagePatchToPost>` установлено поле `NeedReceipt`
- Если документ может использоваться как приглашение к ЭДО, то отправлять его необходимо через метод :doc:`../http/AcquireCounteragent`
