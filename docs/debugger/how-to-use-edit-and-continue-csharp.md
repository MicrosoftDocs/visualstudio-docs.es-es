---
title: "C&#243;mo: Utilizar Editar y continuar (C#) | Microsoft Docs"
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
helpviewer_keywords: 
  - "Editar y continuar [C#], acerca de Editar y continuar"
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Utilizar Editar y continuar (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con Editar y continuar para C\#, puede realizar cambios en el código en modo de interrupción mientras depura.  Los cambios pueden aplicarse sin necesidad de detener y reiniciar la sesión de depuración.  
  
 La opción Editar y continuar se invoca automáticamente cuando se realizan cambios en modo de interrupción, a continuación, hay que elegir un comando de ejecución del depurador, como **Continuar**, **Paso** o **Establecer instrucción siguiente**, o evaluar una función en una ventana del depurador.  
  
> [!NOTE]
>  No se admite Editar y continuar cuando se depura código de Compact Framework, código optimizado, código mixto nativo\/administrado o código de integración de Common Language Runtime \(CLR\) de SQL Server.  En caso de que se intenten aplicar cambios en el código en alguno de estos escenarios, el depurador mostrará un cuadro de diálogo donde se explique que no se admite la opción Editar y continuar.  
  
### Para invocar automáticamente Editar y continuar  
  
1.  En el modo de interrupción, realice un cambio en el código fuente.  
  
2.  En el menú **Depurar**, haga clic en **Continuar**, **Paso** o **Establecer instrucción siguiente** o evalúe una función en una ventana del depurador.  
  
     El código nuevo se compilará y la depuración se reanudará con el código nuevo.  La opción Editar y continuar no admite algunos cambios.  Para obtener más información, vea [Cambios admitidos en el código \(C\#\)](../debugger/supported-code-changes-csharp.md).  
  
### Para habilitar o deshabilitar Editar y continuar  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, expanda el nodo **Depuración** y seleccione **Editar y continuar**.  
  
3.  En la página **Editar y continuar** del cuadro de diálogo **Opciones**, active o desactive la casilla **Habilitar Editar y continuar**.  
  
     La configuración tendrá efecto cuando se reinicie la sesión de depuración.  
  
## Vea también  
 [Editar y continuar \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [Cambios admitidos en el código \(C\#\)](../debugger/supported-code-changes-csharp.md)   
 [Errores y advertencias de Editar y continuar \(C\#\)](../misc/edit-and-continue-errors-and-warnings-csharp.md)