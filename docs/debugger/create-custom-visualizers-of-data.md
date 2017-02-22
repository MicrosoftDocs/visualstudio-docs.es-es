---
title: "Visualizadores | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.visualizer.troubleshoot"
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
  - "depurador, visualizadores"
  - "visualizadores"
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los visualizadores son componentes de la interfaz de usuario del depurador de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Un *visualizador* crea un cuadro de diálogo u otra interfaz para mostrar una variable o un objeto de forma adecuada según su tipo de datos.  Por ejemplo, un visualizador HTML interpreta una cadena HTML y muestra el resultado tal como aparecería en una ventana del explorador; un visualizador de mapa de bits interpreta una estructura de mapa de bits y muestra el gráfico que representa.  Algunos visualizadores permiten modificar y ver los datos.  
  
 El depurador de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] incluye seis visualizadores estándar.  Son los visualizadores de texto, HTML, XML y JSON \(todos ellos funcionan con objetos de cadena\), el visualizador de árboles de WPF, para mostrar las propiedades de un árbol visual de objetos de WPF, y el visualizador de conjuntos de datos, que funciona con objetos DataSet, DataView y DataTable.  Es posible que, en el futuro, haya visualizadores adicionales disponibles para descargar de Microsoft Corporation, de terceros y de la comunidad.  También puede escribir sus propios visualizadores e instalarlos en el depurador de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
> [!NOTE]
>  En las aplicaciones de la **Tienda**, solo se admiten los visualizadores de texto estándar, HTML, XML y JSON.  No se admiten los visualizadores personalizados \(creados por el usuario\).  
  
 Los visualizadores se representan en el depurador mediante un icono de lupa.  Cuando vea el icono de lupa en una **Información sobre datos**, en una ventana de variables del depurador o en el cuadro diálogo **Inspección rápida**, haga clic en el icono y seleccione un visualizador adecuado para el tipo de datos del objeto correspondiente.  
  
 Los visualizadores no se admiten en .NET Compact Framework.  
  
> [!NOTE]
>  Los visualizadores del depurador requieren más privilegios de los permitidos por una aplicación de confianza parcial.  Como resultado, los visualizadores no se cargarán cuando la ejecución se detenga en código con confianza parcial.  Para depurar con un visualizador, debe ejecutar el código con plena confianza.  
  
## En esta sección  
 [Cómo: Escribir un visualizador](../debugger/how-to-write-a-visualizer.md)  
  
 [Tutorial: Escribir un visualizador en C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Cómo: Instalar un visualizador](../debugger/how-to-install-a-visualizer.md)  
  
 [Cómo: Comprobar y depurar un visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referencia de la API del visualizador](../debugger/visualizer-api-reference.md)  
  
## Secciones relacionadas  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)