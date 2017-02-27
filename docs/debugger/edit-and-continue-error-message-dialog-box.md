---
title: "Editar y continuar (Cuadro de di&#225;logo de mensaje de error) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.ENC.SupportedButNotAvaiable"
  - "vs.debug.ENC.CannotEditWhileException"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Editar y continuar (cuadro de diálogo de mensaje de error)"
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Editar y continuar (Cuadro de di&#225;logo de mensaje de error)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo aparece cuando se depura en un lenguaje que admite Editar y continuar, pero **Editar y continuar** no está disponible para el tipo de cambios de código realizados.  El mensaje de error incluido en el cuadro proporciona una explicación más detallada.  Entre las posibles razones para que aparezca este cuadro de diálogo se incluyen:  
  
-   Se intentó editar código administrado cuando estaba habilitada la depuración no administrada.  Editar y continuar no funciona con la depuración en modo mixto.  
  
-   Se intentó editar código de SQL Server.  
  
-   Se intentó editar código mientras se depuraba un volcado de memoria de Dr.  Watson.  
  
-   Se intentó editar código después de que ocurriera una excepción no controlada y no se seleccionó la opción **Desenredar la pila de llamadas de las excepciones no controladas**.  
  
-   Se intentó editar código mientras se depuraba una aplicación incrustada en tiempo de ejecución.  
  
-   Se intentó editar código en un programa al que se asoció, en lugar de comenzar desde el menú **Depurar**.  
  
-   Se intentó editar código optimizado.  
  
-   Se intentó editar código administrado cuando el destino es una aplicación de 64 bits.  Si desea utilizar la opción Editar y continuar, deberá establecer el destino en x86. \(**Propiedades de *Project***, pestaña **Compilar**, **Configuración de compilador avanzada**\).  
  
-   Se intentó editar código en un ensamblado que se modificó durante la depuración y se ha vuelto ha cargar.  
  
-   Se intentó editar código en un ensamblado que no se ha cargado.  
  
-   Se inició la depuración de una versión anterior de la aplicación \(ya que la nueva versión tenía errores de compilación\).  
  
-   Se intentó editar código mientras se estaba ejecutando.  
  
## Lista de UIElement  
 **OK**  
 Sale del cuadro de diálogo y cancela el intento de edición inmediatamente anterior.  
  
## Vea también  
 [Cambios y limitaciones admitidos en el código \(C\+\+\)](../debugger/supported-code-changes-cpp.md)