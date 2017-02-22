---
title: "C&#243;mo: Salir de c&#243;digo administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Ventana Pila de llamadas, ausencia de marcos nativos"
  - "código, código administrado"
  - "marcos nativos"
  - "ejecución paso a paso, fuera del código administrado"
  - "código administrado, ejecución paso a paso fuera"
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Salir de c&#243;digo administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si el código tiene marcos nativos que no se ven en la ventana **Pila de llamadas**, salir de código administrado puede generar resultados inesperados.  Como solución, puede utilizar un punto de interrupción en lugar de **Paso a paso para salir**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para salir de una llamada a código administrado cuando los marcos nativos no se muestran en la pila de llamadas  
  
1.  En el código nativo, establezca un punto de interrupción de ubicación después de la llamada al código administrado.  
  
2.  En el menú **Depurar**, elija **Continuar**.  
  
     Cuando se complete la llamada administrada, la ejecución se interrumpirá en el punto de interrupción del código nativo.  
  
## Vea también  
 [Cómo: Utilizar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)