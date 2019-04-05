---
title: Filtrar Examinar el código del sistema después de una excepción | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 289ef1825e8034566e2a9595a46919a3c498108d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987225"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Filtrar Examinar el código del sistema después de una excepción
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
