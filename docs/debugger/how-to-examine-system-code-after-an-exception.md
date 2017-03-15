---
title: "C&#243;mo: Examinar el c&#243;digo del sistema despu&#233;s de una excepci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar, excepciones"
  - "excepciones, depurar"
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo: Examinar el c&#243;digo del sistema despu&#233;s de una excepci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se produce una excepción, es posible que tenga que examinar el código de una llamada al sistema para determinar su causa.  El procedimiento siguiente explica cómo hacerlo si no se tienen símbolos cargados para el código del sistema o si Sólo mi código está habilitado.  
  
### Para examinar el código del sistema tras una excepción  
  
1.  En la ventana **Pila de llamadas**, haga clic con el botón secundario y, a continuación, haga clic en **Mostrar código externo**.  
  
     Si Sólo mi código no está habilitado, esta opción no está disponible en el menú contextual y de forma predeterminada se muestra el código del sistema.  
  
2.  Haga clic con el botón secundario en los marcos del código externos que ahora aparecen en la ventana **Pila de llamadas**.  
  
3.  Elija **Cargar símbolos desde** y, a continuación, haga clic en **Servidores de símbolos de Microsoft**.  
  
    1.  Si Sólo mi código está habilitado, aparecerá un cuadro de diálogo.  Indica que Sólo mi código se ha deshabilitado.  Esto es necesario para entrar en las llamadas del sistema.  
  
    2.  Aparece el cuadro de diálogo **Descargar símbolos públicos**.  Desaparecerá cuando finalice la descarga.  
  
4.  Ahora puede examinar el código del sistema en la ventana **Pila de llamadas** y otras ventanas.  Por ejemplo, puede hacer doble clic en un marco de pila de llamadas para ver el código en una ventana de origen de datos o **Desensamblado**.  
  
## Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)