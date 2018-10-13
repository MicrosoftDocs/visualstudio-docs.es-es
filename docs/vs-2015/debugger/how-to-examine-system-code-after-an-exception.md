---
title: 'Cómo: examinar el código del sistema después de una excepción | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91b0f0ba806868420b56f59d1b3f6de99a87886b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255780"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Cómo: Examinar el código del sistema después de una excepción
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se produce una excepción, es posible que tenga que examinar el código de una llamada al sistema para determinar su causa. El procedimiento siguiente explica cómo hacerlo si no se tienen símbolos cargados para el código del sistema o si Sólo mi código está habilitado.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Para examinar el código del sistema tras una excepción  
  
1.  En el **pila de llamadas** ventana, el botón derecho, a continuación, haga clic en **mostrar código externo**.  
  
     Si Sólo mi código no está habilitado, esta opción no está disponible en el menú contextual y de forma predeterminada se muestra el código del sistema.  
  
2.  Haga clic en los marcos de código externo que ahora aparecen en la **pila de llamadas** ventana.  
  
3.  Seleccione **cargar símbolos desde** y, a continuación, haga clic en **servidores de símbolos de Microsoft**.  
  
    1.  Si Sólo mi código está habilitado, aparecerá un cuadro de diálogo. Indica que Sólo mi código se ha deshabilitado. Esto es necesario para entrar en las llamadas del sistema.  
  
    2.  El **descargar símbolos públicos** aparece el cuadro de diálogo. Desaparecerá cuando finalice la descarga.  
  
4.  Ahora puede examinar el código del sistema en el **pila de llamadas** ventana y otras ventanas. Por ejemplo, hacer doble clic en un marco de pila de llamadas para ver el código en un origen o **desensamblado** ventana.  
  
## <a name="see-also"></a>Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)





