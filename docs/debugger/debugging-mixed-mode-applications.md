---
title: "Depurar aplicaciones en modo mixto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Pila de llamadas (ventana)"
  - "Pila de llamadas (ventana), depuración en modo mixto"
  - "depurar [Visual Studio], modo mixto"
  - "depurar código administrado, código mixto"
  - "depuración en modo mixto"
  - "depuración en modo mixto, pila de llamadas"
  - "depuración en modo mixto, evaluación de propiedades"
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar aplicaciones en modo mixto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una aplicación en modo mixto es cualquier aplicación que combine código nativo \(C\+\+\) y código administrado \(como Visual Basic, Visual C\# o C\+\+ administrado que se ejecute en Common Language Runtime\).  La depuración de aplicaciones en modo mixto es un proceso en gran medida transparente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; no difiere mucho de la depuración de una aplicación en modo individual.  Sin embargo, existen consideraciones especiales.  
  
## Habilitar Editar y continuar de C\+\+ en la depuración en modo mixto  
  
-   Para usar Editar y Continuar para C\+\+ en Visual Studio 2013, tiene que revertir al motor de depuración heredado.  Vea [Cambiar al modo de compatibilidad administrado en Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) en el blog Microsoft Application Lifecycle Management.  
  
## Evaluación de propiedades en aplicaciones en modo mixto  
 En las aplicaciones en modo mixto, la evaluación de propiedades por parte del depurador es una operación costosa.  En consecuencia, las operaciones de depuración como la ejecución paso a paso pueden parecer lentas.  Para obtener más información, vea [Ejecutar instrucciones paso a paso](http://msdn.microsoft.com/es-es/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  Si se produce un rendimiento muy bajo en la depuración en modo mixto, puede desactivar la evaluación de propiedades en las ventanas del depurador.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### Para desactivar la evaluación de propiedades  
  
1.  En el menú **Herramientas**, elija **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, abra la carpeta **Depuración** y seleccione la categoría **General**.  
  
3.  Desactive la casilla **Habilitar evaluación de propiedades y otras llamadas a función implícitas**.  
  
 Puesto que las pilas de llamadas nativas y las administradas son diferentes, el depurador no siempre proporciona la pila de llamadas competa para el código mixto.  Cuando el código nativo llama a código administrado, quizá observe algunas discrepancias.  Para obtener más información, vea [Código mixto e información no mostrada en la ventana Pila de llamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)