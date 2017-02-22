---
title: "C&#243;mo: Depurar en modo mixto | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "depurar [Visual Studio], modo mixto"
  - "depurar las DLL"
  - "depuración en modo mixto"
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar en modo mixto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los procedimientos siguientes describen cómo depurar código administrado y nativo, también conocido como depuración en modo mixto.  Existen dos escenarios para hacerlo, en función de que el archivo DLL o la aplicación se hayan escrito en código nativo:  
  
-   La aplicación que realiza la llamada al archivo DLL está escrita en código nativo.  En este caso, el código del archivo DLL será administrado y deberán habilitarse tanto los depuradores administrados como los nativos para depurar ambos tipos de código.  Puede comprobarlo en el cuadro de diálogo **Páginas de propiedades de \<Proyecto\>**.  La forma de hacerlo depende de si inicia la depuración desde el proyecto DLL o desde el proyecto de la aplicación que hace la llamada.  
  
-   La aplicación que realiza la llamada al archivo DLL está escrita en código administrado y el archivo DLL está escrito en código nativo.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para habilitar la depuración en modo mixto  
  
1.  En el **Explorador de soluciones**, seleccione el proyecto.  
  
2.  En el menú **Ver**, haga clic en **Páginas de propiedades**.  
  
3.  En el cuadro de diálogo **Páginas de propiedades de \<proyecto \>**, expanda el nodo **Propiedades de configuración** y, a continuación, seleccione **Depuración**.  
  
4.  Establezca el **Tipo de depurador** en **Mixto** o **Automático**.  
  
## Vea también  
 [Cómo: Depurar desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md)