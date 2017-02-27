---
title: "C&#243;mo: Mostrar informaci&#243;n de seguimiento de WPF | Microsoft Docs"
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
  - "depurar, WPF"
  - "WPF, depurar"
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo: Mostrar informaci&#243;n de seguimiento de WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] puede recibir información de seguimiento de la depuración de las aplicaciones WPF y mostrar esa información en la **Ventana de salida**.  Para mostrar la información de seguimiento de depuración, debe estar habilitada la traza de WPF.  
  
 Puede habilitar la traza de WPF en su archivo App.Config o, mediante programación, utilizando la clase <xref:System.Diagnostics.PresentationTraceSources>.  Una manera más fácil de habilitar la traza de WPF es usar la ventana **Opciones**.  No se admite la traza WPF en las aplicaciones web.  
  
### Para habilitar o personalizar la información de seguimiento de WPF  
  
1.  En el menú **Herramientas**, elija **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, en el cuadro de la izquierda, abra el nodo **Depuración**.  
  
3.  En **Depuración**, haga clic en **Ventana de salida**.  
  
4.  En **Configuración general de salida**, seleccione **Toda la salida de depuración**.  
  
5.  En el cuadro de la derecha, busque **Configuración de seguimiento de WPF**.  
  
6.  Abra el nodo **Configuración de seguimiento de WPF**.  
  
7.  En **Configuración de seguimiento de WPF**, haga clic en la categoría de valores que desea habilitar \(por ejemplo, **Enlace de datos**\).  
  
     Aparecerá un control de lista desplegable en la columna Configuración, al lado de **Enlace de datos** o de la categoría en la que haya hecho clic.  
  
8.  Haga clic en la lista desplegable y seleccione el tipo de información de seguimiento que desea ver: **All**, **Critical**, **Error**, **Warning**, **Information**, **Verbose** o **ActivityTracing**.  
  
     **Critical** sólo habilita la traza de los eventos críticos.  
  
     **Error** habilita la traza de los eventos críticos y de error.  
  
     **Warning** habilita la traza de los eventos críticos, de error y de advertencia.  
  
     **Information** habilita la traza de los eventos críticos, de error, de advertencia y de información.  
  
     **Verbose** habilita la traza de los eventos críticos, de error, de advertencia, de información y detallados.  
  
     **ActivityTracing** habilita la traza de los eventos de detención, inicio, suspensión, transferencia y reanudación.  
  
     Para obtener más información sobre el significado de estos niveles de información de seguimiento, vea <xref:System.Diagnostics.SourceLevels>.  
  
9. Haga clic en **Aceptar**.  
  
### Para deshabilitar la información de seguimiento de WPF  
  
1.  En el menú **Herramientas**, elija **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, en el cuadro de la izquierda, abra el nodo **Depuración**.  
  
3.  En **Depuración**, haga clic en **Ventana de salida**.  
  
4.  En el cuadro de la derecha, busque **Configuración de seguimiento de WPF**.  
  
5.  Abra el nodo **Configuración de seguimiento de WPF**.  
  
6.  En **Configuración de seguimiento de WPF**, haga clic en la categoría de valores que desea habilitar \(por ejemplo, **Enlace de datos**\).  
  
     Aparecerá un control de lista desplegable en la columna Configuración, al lado de **Enlace de datos** o de la categoría en la que haya hecho clic.  
  
7.  Haga clic en la lista desplegable y seleccione **Desactivado**.  
  
8.  Haga clic en **Aceptar**.  
  
## Vea también  
 [Depurar WPF](../debugger/debugging-wpf.md)