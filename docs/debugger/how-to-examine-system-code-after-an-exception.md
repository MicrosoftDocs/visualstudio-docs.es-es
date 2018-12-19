---
title: Examinar el código del sistema después de una excepción | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: f2e3de04d07ffe1bf2853113cb003a273fa9e5a7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050997"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Procedimiento Examinar el código del sistema después de una excepción
Cuando se produce una excepción, es posible que tenga que examinar el código de una llamada al sistema para determinar su causa. El procedimiento siguiente explica cómo hacerlo si no se tienen símbolos cargados para el código del sistema o si Sólo mi código está habilitado.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Para examinar el código del sistema tras una excepción  
  
1.  En la ventana **Pila de llamadas**, haga clic con el botón derecho y, a continuación, haga clic en **Mostrar código externo**.  
  
     Si Sólo mi código no está habilitado, esta opción no está disponible en el menú contextual y de forma predeterminada se muestra el código del sistema.  
  
2.  Haga clic con el botón derecho en los marcos del código externos que ahora aparecen en la ventana **Pila de llamadas**.  
  
3.  Elija **Cargar símbolos desde** y, a continuación, haga clic en **Servidores de símbolos de Microsoft**.  
  
    1.  Si Sólo mi código está habilitado, aparecerá un cuadro de diálogo. Indica que Sólo mi código se ha deshabilitado. Esto es necesario para entrar en las llamadas del sistema.  
  
    2.  Aparece el cuadro de diálogo **Descargar símbolos públicos**. Desaparecerá cuando finalice la descarga.  
  
4.  Ahora puede examinar el código del sistema en la ventana **Pila de llamadas** y otras ventanas. Por ejemplo, puede hacer doble clic en un marco de pila de llamadas para ver el código en una ventana de origen de datos o **Desensamblado**.  
  
## <a name="see-also"></a>Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)