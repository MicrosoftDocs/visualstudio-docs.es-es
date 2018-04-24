---
title: Cuadro de diálogo (excepción) del depurador de Microsoft Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24ccb3de6b22f54b239b5b772490a8d05a990dbd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Depurador de Microsoft Visual Studio: se inició una excepción (cuadro de diálogo)
Se ha producido una excepción en el programa. Este cuadro de diálogo informa sobre la clase de excepción producida. El código necesita tratar esta excepción. Puede elegir entre las siguientes opciones para controlar la excepción:  
  
 **Break**  
 Permite a la ejecución interrumpir el depurador. El controlador de excepciones no se invoca antes de la interrupción. Si continúa desde la interrupción, se invocará al controlador de excepciones.  
  
 **Continue**  
 Permite que continúe la ejecución y ofrece al controlador de excepciones una oportunidad para controlar la excepción. Esta opción no está disponible para algunos tipos de excepciones. **Continuar** permitirá que la aplicación pueda continuar. En una aplicación nativa, se volverá a producir la excepción. En una aplicación administrada, hará que el programa termine o que una aplicación host controle la excepción.  
  
> [!NOTE]
>  No es posible continuar después de una excepción no controlada en el código administrado. Elegir **continuar** después de una excepción no controlada en código administrado, la depuración se detendrá.  
  
 **Pasar por alto**  
 Permite que la ejecución continúe sin invocar al controlador de excepciones. Puesto que no se invoca al controlador de excepciones, puede provocar otras consecuencias, tales como errores y excepciones adicionales. Esta opción no está disponible para algunos tipos de excepciones.  
  
## <a name="see-also"></a>Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)   
 [Procedimientos recomendados para excepciones](/dotnet/standard/exceptions/best-practices-for-exceptions)   
 [Control de excepciones](/cpp/windows/exception-handling-cpp-component-extensions)