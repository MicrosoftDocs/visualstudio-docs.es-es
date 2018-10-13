---
title: Personalización de las comprobaciones nativas en tiempo de ejecución | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 906aca3071c9abc6bd06ac1f0dc4d75bd1920a61
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300890"
---
# <a name="native-run-time-checks-customization"></a>Personalización de las comprobaciones nativas en tiempo de ejecución
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se compila con **/RTC** (comprueba el tiempo de ejecución) o usar el `runtime_checks` pragma, la biblioteca de tiempo de ejecución de C proporciona comprobaciones nativas en tiempo de ejecución. En algunos casos puede ser conveniente personalizar las comprobaciones en tiempo de ejecución:  
  
-   Para enviar los mensajes de comprobación en tiempo de ejecución a un archivo o a un destino distinto del predeterminado.  
  
-   Para especificar un destino de salida para los mensajes de comprobación en tiempo de ejecución en un depurador de otro proveedor.  
  
-   Para generar mensajes de comprobación en tiempo de ejecución desde un programa compilado con una versión de distribución de la biblioteca en tiempo de ejecución de C. Las versiones de distribución de la biblioteca no utilizan `_CrtDbgReportW` para generar informes de errores en tiempo de ejecución. En su lugar, mostrará un **Assert** cuadro de diálogo para cada error de tiempo de ejecución.  
  
 Para personalizar la comprobación de errores en tiempo de ejecución, puede:  
  
-   Escriba una función que crea un informe de error en tiempo de ejecución. Para obtener más información, consulte [Cómo: escribir una función de notificación de Error de tiempo de ejecución](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   Personalizar el destino del mensaje de error.  
  
-   Consultar información sobre los errores de comprobación en tiempo de ejecución.  
  
## <a name="customize-the-error-message-destination"></a>Personalizar el destino de los mensajes de error  
 Si utiliza `_CrtDbgReportW` para generar informes de errores, puede usar `_CrtSetReportMode` para especificar el destino de los mensajes de error.  
  
 Si usa una función de generación de informes personalizada, utilice `_RTC_SetErrorType` para asociar un error a un tipo de informe.  
  
## <a name="query-for-information-about-run-time-checks"></a>Consultar información acerca de las comprobaciones en tiempo de ejecución  
 `_RTC_NumErrors` devuelve el número de tipos de errores detectados por las comprobaciones de errores en tiempo de ejecución. Para obtener una breve descripción de cada error, puede recorrer con un bucle desde 0 al valor devuelto `_RTC_NumErrors`, pasando el valor de la iteración a `_RTC_GetErrDesc` en cada bucle. Para obtener más información, consulte [_RTC_NumErrors](http://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) y [_RTC_GetErrDesc](http://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: utilizar comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)





