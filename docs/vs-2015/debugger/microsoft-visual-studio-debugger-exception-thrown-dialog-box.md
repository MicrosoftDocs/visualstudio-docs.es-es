---
title: Microsoft Visual Studio del depurador (excepción) cuadro de diálogo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3fec8fd6bc00199fc2a0d5193d7f7534acca754
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383936"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Depurador de Microsoft Visual Studio: se inició una excepción (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se ha producido una excepción en el programa. Este cuadro de diálogo informa sobre la clase de excepción producida. El código necesita tratar esta excepción. Puede elegir entre las siguientes opciones para controlar la excepción:  
  
 **Break**  
 Permite a la ejecución interrumpir el depurador. El controlador de excepciones no se invoca antes de la interrupción. Si continúa desde la interrupción, se invocará al controlador de excepciones.  
  
 **Continue**  
 Permite que continúe la ejecución y ofrece al controlador de excepciones una oportunidad para controlar la excepción. Esta opción no está disponible para algunos tipos de excepciones. **Continuar** permitirá que la aplicación siga adelante. En una aplicación nativa, se volverá a producir la excepción. En una aplicación administrada, hará que el programa termine o que una aplicación host controle la excepción.  
  
> [!NOTE]
> No es posible continuar después de una excepción no controlada en el código administrado. Si elige **Continuar** después de una excepción no controlada en código administrado, la depuración se detendrá.  
  
 **Ignorar**  
 Permite que la ejecución continúe sin invocar al controlador de excepciones. Puesto que no se invoca al controlador de excepciones, puede provocar otras consecuencias, tales como errores y excepciones adicionales. Esta opción no está disponible para algunos tipos de excepciones.  
  
## <a name="see-also"></a>Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)   
 [Procedimientos recomendados para excepciones](http://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Control de excepciones](http://msdn.microsoft.com/library/ccb11fe8-6938-41ac-b477-a183e85865b9)
