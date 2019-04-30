---
title: Microsoft Visual Studio del depurador (excepción) cuadro de diálogo | Documentos de Microsoft
titleSuffix: ''
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a684002360f59d33e61c40261afc1bfd515511e3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408523"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Depurador de Microsoft Visual Studio: se inició una excepción (cuadro de diálogo)
Se ha producido una excepción en el programa. Este cuadro de diálogo informa sobre la clase de excepción producida. El código necesita tratar esta excepción. Puede elegir entre las siguientes opciones para controlar la excepción:

 **Salto** permite la ejecución interrumpir el depurador. El controlador de excepciones no se invoca antes de la interrupción. Si continúa desde la interrupción, se invocará al controlador de excepciones.

 **Continuar** permite la ejecución continuar, lo que proporciona el controlador de excepciones una oportunidad para controlar la excepción. Esta opción no está disponible para algunos tipos de excepciones. **Continuar** permitirá que la aplicación siga adelante. En una aplicación nativa, se volverá a producir la excepción. En una aplicación administrada, hará que el programa termine o que una aplicación host controle la excepción.

> [!NOTE]
> No es posible continuar después de una excepción no controlada en el código administrado. Si elige **Continuar** después de una excepción no controlada en código administrado, la depuración se detendrá.

 **Omitir** permite la ejecución continúe sin invocar el controlador de excepciones. Puesto que no se invoca al controlador de excepciones, puede provocar otras consecuencias, tales como errores y excepciones adicionales. Esta opción no está disponible para algunos tipos de excepciones.

## <a name="see-also"></a>Vea también
- [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)
- [Procedimientos recomendados para excepciones](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Control de excepciones](/cpp/windows/exception-handling-cpp-component-extensions)