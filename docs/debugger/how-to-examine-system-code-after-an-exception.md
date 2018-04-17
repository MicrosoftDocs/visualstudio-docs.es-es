---
title: 'Cómo: examinar el código del sistema después de una excepción | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2914aab911d3c700b38c58eac009b2e21e94420e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Cómo: Examinar el código del sistema después de una excepción
Cuando se produce una excepción, es posible que tenga que examinar el código de una llamada al sistema para determinar su causa. El procedimiento siguiente explica cómo hacerlo si no se tienen símbolos cargados para el código del sistema o si Sólo mi código está habilitado.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Para examinar el código del sistema tras una excepción  
  
1.  En el **pila de llamadas** ventana, contextual y, a continuación, haga clic en **mostrar código externo**.  
  
     Si Sólo mi código no está habilitado, esta opción no está disponible en el menú contextual y de forma predeterminada se muestra el código del sistema.  
  
2.  Haga clic en los marcos del código externos que ahora aparecen en la **pila de llamadas** ventana.  
  
3.  Seleccione **cargar símbolos desde** y, a continuación, haga clic en **servidores de símbolos de Microsoft**.  
  
    1.  Si Sólo mi código está habilitado, aparecerá un cuadro de diálogo. Indica que Sólo mi código se ha deshabilitado. Esto es necesario para entrar en las llamadas del sistema.  
  
    2.  El **descargar símbolos públicos** aparece el cuadro de diálogo. Desaparecerá cuando finalice la descarga.  
  
4.  Ahora puede examinar el código del sistema en el **pila de llamadas** ventana y otras ventanas. Por ejemplo, hacer doble clic en un marco de pila de llamadas para ver el código de un origen o **desensamblado** ventana.  
  
## <a name="see-also"></a>Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)