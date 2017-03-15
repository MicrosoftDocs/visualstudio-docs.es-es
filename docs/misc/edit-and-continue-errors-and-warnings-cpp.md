---
title: "Errores y advertencias de Editar y continuar (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENC2001"
  - "ENC1006"
  - "ENC2008"
  - "ENC1009"
  - "ENC1002"
  - "ENC2002"
  - "ENC1011"
  - "ENC1003"
  - "ENC1004"
  - "ENC1008"
  - "ENC1013"
  - "ENC2005"
  - "ENC1010"
  - "ENC2004"
  - "ENC1007"
  - "ENC1005"
  - "ENC2006"
  - "ENC1001"
  - "ENC2007"
  - "ENC2003"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Editar y continuar [C++], errores y advertencias"
  - "errores [C++], Editar y continuar"
  - "errores [depurador], Editar y continuar"
ms.assetid: b5c5e25c-7ca4-4ca9-b91e-e8882de44dae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# Errores y advertencias de Editar y continuar (C++)
La característica Editar y continuar de [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] permite detener la ejecución del programa en el modo de interrupción, realizar cambios en el código en ejecución y, a continuación, reanudar la ejecución del programa con estos nuevos cambios incorporados.  
  
 Las modificaciones del código declarativo que afectan a la estructura pública de una clase suelen estar prohibidas, y no se permiten algunas modificaciones que se podrían hacer en un método, cuerpo de propiedad o declaraciones privadas en una clase.  Siempre que es posible, Editar y continuar marca el código que no se puede editar en gris claro y muestra un mensaje de error.  Para obtener más información sobre las ediciones no compatibles con la característica Editar y continuar de [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)], vea [Editar y continuar \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md).  
  
 Los errores y advertencias de Editar y Continuar se pueden resolver de una de las siguientes maneras:  
  
|Solución|Números de mensajes de error y advertencia|  
|--------------|------------------------------------------------|  
|Detenga la depuración, vuelva a aplicar los cambios y, a continuación, reanude la depuración.|1001, 1002, 1003, 1004, 1005, 1006, 1007, 1008, 1010, 1013, 2003, 2005. Para obtener una lista de mensajes de error y advertencia de esta categoría, vea [Reiniciar mensajes de depuración](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_RestartDebuggingMessages).|  
|En el menú **Edición**, elija **Deshacer** y, a continuación, continúe la depuración con el código sin cambios.<br /><br /> O bien<br /><br /> Detenga la depuración, vuelva a aplicar los cambios y, a continuación, reanude la depuración.|1009, 1011. Para obtener una lista de mensajes de error y advertencia de esta categoría, vea [Deshacer o detener mensajes](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_UndoOrStopMessages).|  
|Continúe la depuración.  Los cambios se omitirán la primera vez que se encuentre el código, pero se aplicarán en las llamadas subsiguientes.|2001, 2002, 2004.  Para obtener una lista de mensajes de error y advertencia de esta categoría, vea [Aplicar en los siguientes mensajes de llamada](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_ApplyAtNextCallMessages).|  
|Realice otra acción, por ejemplo restaurar los puntos de interrupción o recompilar los módulos con la versión actual de [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)].|2007, 2008.  Para obtener una lista de mensajes de error y advertencia de esta categoría, vea [Otros mensajes de acción necesarios](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_OtherActionRequiredMessages)|  
  
##  <a name="BKMK_RestartDebuggingMessages"></a> Reiniciar mensajes de depuración  
 Los siguientes mensajes de error se deben resolver deteniendo la sesión de depuración actual, volviendo a aplicar los cambios realizados y, a continuación, reiniciando la sesión de depuración.  
  
|||  
|-|-|  
|1001|No se puede actualizar el procesador para el símbolo: *symbol* \(loc: *location*, thunk: *address*\)|  
|1002|Símbolo de datos cambiado: símbolo \(*symbol*\)|  
|1003|No se puede asignar el código thunk para la nueva función: *function*|  
|1004|No se puede abrir PDB para empaquetado tipo: *pdb* \(pdb\)|  
|1005|Símbolo cambiado de nombre, quitado o modificado: *symbol*|  
|1006|Una variable global o estática se ha agregado, cambiado de nombre, quitado o ha cambiado el tipo de datos o la inicialización: *symbol* \(referenciado por: *module*\)|  
|1007|Símbolo no definido: *symbol* \(referenciado por: *module*\)|  
|1008|No se puede realizar una inicialización en tiempo de ejecución requerida por el objeto cargado durante la edición: *module*|  
|1010|Variable global o estática agregada: *variable referenced in file*|  
|1013|Memoria insuficiente en el depurador al aplicar cambios de código.|  
|2003|El cambio en la posición del código puede causar control de excepciones o errores variables de destrucción: *function*|  
|2005|El nuevo origen contribuye al código.  Puede afectar a la información del número de línea del depurador: función \(*function*\)|  
  
##  <a name="BKMK_UndoOrStopMessages"></a> Deshacer o detener mensajes  
 Los siguientes mensajes de error se pueden resolver deteniendo la sesión de depuración actual, volviendo a aplicar los cambios realizados y, a continuación, reiniciando la sesión de depuración.  
  
-   En el menú Edición, haga clic en Deshacer.  Puede reanudar la depuración, pero las modificaciones no se aplican.  
  
     O bien  
  
-   Detenga la depuración, vuelva a aplicar las modificaciones y, a continuación, reinicie la depuración.  
  
|||  
|-|-|  
|1009|Variable global o estática eliminada: *variable referenced in file*|  
|1011|Variable global o estática cambiada: *variable referenced in file*|  
  
##  <a name="BKMK_ApplyAtNextCallMessages"></a> Aplicar en los siguientes mensajes de llamada  
 Puede continuar la sesión de depuración si aparece uno de los siguientes mensajes de advertencia.  Las modificaciones no se aplicarán si se llama por primera vez al código después de la modificación; las modificaciones se aplicarán en todas las llamadas al código subsiguientes.  
  
|||  
|-|-|  
|2001|No se puede encontrar variable local o tipo de variable de datos cambiada: símbolo \(*symbol*\)|  
|2002|Variable eliminada o nueva variable local requiere construcción o destrucción: símbolo \(*symbol*\)|  
|2004|No se puede agregar ni quitar una variable local con un nombre definido más de una vez: símbolo \(*symbol*\)|  
  
##  <a name="BKMK_OtherActionRequiredMessages"></a> Otros mensajes de acción necesarios  
 La acción necesaria para resolver estos mensajes se describe después del texto del mensaje.  
  
|||  
|-|-|  
|2007|No se pueden mover algunos puntos de interrupción de la ventana Desensamblado.<br /><br /> Para resolver este problema, restablezca los puntos de interrupción afectados.|  
|2008|No se pueden cargar símbolos de depuración para archivo *file* en módulo *module*.<br /><br /> Para resolver este problema, recompile el módulo especificado con la versión actual de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].|  
  
## Vea también  
 [Editar y continuar \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md)   
 [Editar y continuar](../debugger/edit-and-continue.md)