---
title: "C&#243;mo: Depurar c&#243;digo fuente de .NET Framework | Microsoft Docs"
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
helpviewer_keywords: 
  - "depurar, código fuente de .NET Framework"
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar c&#243;digo fuente de .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La versión más reciente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona nuevas características para la depuración en [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Para depurar el código fuente de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], debe tener acceso a los símbolos de depuración del código.  También necesita habilitar la ejecución paso a paso del código fuente de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Puede habilitar la ejecución paso a paso y la descarga de símbolos de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en el cuadro de diálogo **Opciones**.  Al habilitar la descarga de símbolos, puede descargarlos inmediatamente o habilitar la opción para una descarga posterior.  Si no los descarga inmediatamente, los símbolos se descargarán la próxima vez que inicie la depuración de la aplicación.  También puede hacer una descarga manual de la ventana **Módulos** o la ventana **Pila de llamadas**.  
  
### Para habilitar la depuración de código fuente de .NET Framework  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, haga clic en la categoría **Depuración**.  
  
3.  En el cuadro **General**, seleccione **Habilitar ejecución paso a paso de código fuente de .NET Framework**.  
  
    1.  Si tenía habilitada la opción Sólo mi código , un cuadro de diálogo de advertencia le indicará que dicha opción se ha deshabilitado.  Haga clic en **Aceptar**.  
  
    2.  Si no tenía una ubicación de caché de símbolos establecida, otro cuadro de diálogo de advertencia le indicará que se ha establecido una ubicación de caché de símbolos predeterminada.  Haga clic en **Aceptar**.  
  
4.  En la categoría **Depuración**, haga clic en **Símbolos**.  
  
5.  Si desea cambiar la ubicación en caché de los símbolos:  
  
    1.  Abra el nodo **Depuración** en el cuadro de la izquierda.  
  
    2.  Bajo el nodo **Depuración**, haga clic en **Símbolos**.  
  
    3.  Edite la ubicación en **Almacenar símbolos en caché desde los servidores de símbolos a este directorio** o haga clic en **Examinar** para elegir una ubicación.  
  
6.  Si desea descargar inmediatamente los símbolos, haga clic en **Cargar símbolos de las ubicaciones indicadas**.  
  
     Este botón no está disponible en modo de diseño.  
  
     Si decide no descargar ahora los símbolos, estos se descargarán automáticamente la próxima vez que inicie la depuración del programa.  
  
7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  
  
### Para cargar símbolos de Framework mediante la ventana Módulos  
  
1.  En la ventana **Módulos**, haga clic con el botón secundario en un módulo para el que no se cargan los símbolos.  Puede saber si se cargan los símbolos examinando la columna **Estado del símbolo**.  
  
2.  Elija **Cargar símbolos desde** y haga clic en **Servidores de símbolos de Microsoft** para descargar los símbolos del servidor de símbolos público de Microsoft, o **Ruta de acceso de símbolos** para cargarlos desde un directorio en el que haya almacenado previamente los símbolos.  
  
### Para cargar símbolos de Framework mediante la ventana Pila de llamadas  
  
1.  En la ventana **Pila de llamadas**, haga clic con el botón secundario en el marco para el cual no están cargados los símbolos.  Este marco se oscurecerá.  
  
2.  Elija **Cargar símbolos desde** y haga clic en **Servidores de símbolos de Microsoft** o **Ruta de acceso de símbolos**.  
  
## Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)