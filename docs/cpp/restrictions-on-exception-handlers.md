---
title: "Restrictions on Exception Handlers"
ms.date: "11/04/2016"
helpviewer_keywords: ["restrictions, exception handlers", "exception handling [C++], exception handlers"]
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
---
# Restrictions on Exception Handlers

The principal limitation to using exception handlers in code is that you cannot use a **goto** statement to jump into a **__try** statement block. Instead, you must enter the statement block through normal flow of control. You can jump out of a **__try** statement block and nest exception handlers as you choose.

## See also

[Writing an Exception Handler](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)