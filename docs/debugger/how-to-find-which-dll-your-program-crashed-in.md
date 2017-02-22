---
title: "C&#243;mo: Averiguar en qu&#233; archivo DLL se bloque&#243; el programa | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, bloqueos de archivos DLL"
  - "depurar [Visual Studio], bloqueos de archivos DLL"
  - "DLL, orden de carga"
  - "errores [depurador], bloqueos de archivos DLL"
  - "Lista de módulos (cuadro de diálogo)"
  - "Módulos (ventana)"
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Averiguar en qu&#233; archivo DLL se bloque&#243; el programa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar su configuración, elija Importar y exportar configuraciones, en el menú Herramientas.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si la aplicación se bloquea durante una llamada a un archivo DLL del sistema o el código de un tercero, es necesario que encuentre qué archivo DLL estaba activo cuando ocurrió el bloqueo.  Si se produce un bloqueo de un archivo DLL fuera de su programa, puede identificar la ubicación mediante la ventana **Módulos**.  
  
### Para averiguar dónde se produjo un bloqueo mediante la ventana Módulos  
  
1.  Anote la dirección donde se produjo el bloqueo.  
  
2.  En el menú **Depurar**, elija **Ventanas** y haga clic en **Módulos**.  
  
3.  En la ventana **Módulos**, busque la columna **Dirección** Es posible que necesite utilizar la barra de desplazamiento para verla.  
  
4.  Haga clic en el botón **Dirección** en la parte superior de la columna para ordenar los archivos DLL por dirección.  
  
5.  Busque en la lista ordenada el archivo DLL cuyo intervalo de direcciones contiene la ubicación del bloqueo.  
  
6.  Consulte las columnas **Nombre** y **Ruta de acceso** para ver el nombre y la ruta del archivo DLL.  
  
## Vea también  
 [Cómo: Depurar DLL nativas](../debugger/how-to-debug-native-dlls.md)   
 [Cómo: Utilizar la ventana Módulos](../debugger/how-to-use-the-modules-window.md)