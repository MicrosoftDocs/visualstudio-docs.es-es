---
title: 'Depurador de Microsoft Visual Studio: se inició una excepción (cuadro de diálogo) | Microsoft Docs'
titleSuffix: ''
description: 'Obtenga información sobre qué hacer cuando se produzca una excepción que el programa deba gestionar. Puede realizar lo siguiente: 1) interrumpir el depurador, 2) continuar o 3) ignorar la excepción.'
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2982912a0bf165f25b7777311d6db9a1bbe01a8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930283"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Depurador de Microsoft Visual Studio: se inició una excepción (cuadro de diálogo)
Se ha producido una excepción en el programa. Este cuadro de diálogo informa sobre la clase de excepción producida. El código necesita tratar esta excepción. Puede elegir entre las siguientes opciones para controlar la excepción:

 **Interrumpir** Permite a la ejecución interrumpir el depurador. El controlador de excepciones no se invoca antes de la interrupción. Si continúa desde la interrupción, se invocará al controlador de excepciones.

 **Continuar** Permite que continúe la ejecución y ofrece al controlador de excepciones una oportunidad para controlar la excepción. Esta opción no está disponible para algunos tipos de excepciones. **Continuar** permitirá que la aplicación siga adelante. En una aplicación nativa, se volverá a producir la excepción. En una aplicación administrada, hará que el programa termine o que una aplicación host controle la excepción.

> [!NOTE]
> No es posible continuar después de una excepción no controlada en el código administrado. Si elige **Continuar** después de una excepción no controlada en código administrado, la depuración se detendrá.

 **Ignorar** Permite que la ejecución continúe sin invocar al controlador de excepciones. Puesto que no se invoca al controlador de excepciones, puede provocar otras consecuencias, tales como errores y excepciones adicionales. Esta opción no está disponible para algunos tipos de excepciones.

## <a name="see-also"></a>Vea también
- [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)
- [Procedimientos recomendados para excepciones](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Control de excepciones](/cpp/extensions/exception-handling-cpp-component-extensions)