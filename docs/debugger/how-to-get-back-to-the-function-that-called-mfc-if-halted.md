---
title: "C&#243;mo: Volver a la funci&#243;n que llam&#243; a MFC cuando est&#225; detenido | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.mfc"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Interrumpir (comando)"
  - "depurar [MFC], funciones"
  - "depurar [MFC], regresar a la función de llamada"
  - "llamadas a funciones, regresar a la función de llamada"
  - "funciones [C++], depurar"
  - "funciones [depurador]"
  - "programas, detener"
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# C&#243;mo: Volver a la funci&#243;n que llam&#243; a MFC cuando est&#225; detenido
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar su configuración, elija Importar y exportar configuraciones, en el menú Herramientas.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si ha utilizado el comando **Interrumpir** del menú **Depurar** para detener el programa y ha terminado en MFC, y está seguro de que el problema se encuentra en el código, puede usar la ventana Pila de llamadas para volver a la función.  Para obtener más información, vea [Cómo: Utilizar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 A veces el código puede interrumpir el bombeo de mensajes.  En ese caso, no hay ningún código de usuario en la pila de llamadas.  Para evitar este problema, puede utilizar puntos de interrupción \(posiblemente con condiciones y números de llamadas\) en lugar del comando **Interrumpir**.  Para obtener más información, vea [Breakpoints and Tracepoints](http://msdn.microsoft.com/es-es/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### Para navegar a la función desde la que se llamó a MFC  
  
-   Utilice la ventana **Pila de llamadas**.  
  
## Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)