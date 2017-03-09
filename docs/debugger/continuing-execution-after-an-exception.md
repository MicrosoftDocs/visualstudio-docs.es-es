---
title: "Continuar la ejecuci&#243;n despu&#233;s de una excepci&#243;n | Microsoft Docs"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, excepciones"
  - "control de excepciones, continuar la ejecución después de"
  - "Excepciones (cuadro de diálogo)"
  - "excepciones, continuar la ejecución después de"
  - "ejecución, continuar después de una excepción"
  - "código administrado, control de excepciones"
  - "excepciones administradas, continuar la ejecución después de"
  - "ejecución de programas"
  - "programas, ejecutar"
  - "subprocesamiento [Visual Studio], continuar la ejecución después de producirse excepciones"
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Continuar la ejecuci&#243;n despu&#233;s de una excepci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando el depurador interrumpe la ejecución debido a una excepción, aparece un cuadro de diálogo.  En el caso de Visual Basic o C\#, se mostrará el cuadro de diálogo [Exception Assistant](../Topic/Exception%20Assistant.md) de forma predeterminada.  En el caso de C\+\+, aparecerá el cuadro de diálogo **Excepción** anterior.  Si utiliza Visual Basic o C\# pero tiene deshabilitado el **Asistente de excepciones** en el cuadro de diálogo **Opciones**, se mostrará el cuadro de diálogo **Excepción**.  
  
 Cuando aparezca el cuadro de diálogo **Asistente de excepciones** o **Excepción**, puede intentar corregir el problema que produjo la excepción.  
  
## Código administrado  
 En el código administrado, puede continuar la ejecución en el mismo subproceso después de que se haya producido una excepción no controlada.  El **Asistente de excepciones** desenreda la pila de llamadas en el punto donde se produjo la excepción.  
  
## Código nativo  
 En C\/C\+\+ nativo, tiene dos opciones:  
  
-   Puede hacer clic en **Interrumpir** e intentar corregir el problema.  Mientras se encuentra en el modo de interrupción, puede desenredar la pila de llamadas haciendo clic con el botón secundario en un marco de la ventana **Pila de llamadas** y seleccionando **Desenredar hasta este marco** en el menú contextual.  Si continúa con la depuración y no ha corregido el problema, volverá a aparecer el cuadro de diálogo **Excepción**.  De lo contrario, el cuadro de diálogo **Excepción** no volverá a aparecer.  
  
-   Puede hacer clic en **Continuar** para continuar la ejecución sin intentar corregir el problema.  Volverá a aparecer el cuadro de diálogo **Excepción**.  
  
## Código mixto  
 Si se produce una excepción no controlada durante la depuración de código mixto nativo y administrado, las restricciones de sistema operativo impedirán que se desenrede la pila de llamadas.  Si intenta rebobinar la pila de llamadas mediante el menú contextual, aparecerá un mensaje de error que indica que el depurador no puede desenredar la pila de llamadas si se ha producido una excepción no controlada durante la depuración de código mixto.  
  
## Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)