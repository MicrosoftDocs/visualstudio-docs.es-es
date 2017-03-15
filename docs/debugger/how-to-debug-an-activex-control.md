---
title: "C&#243;mo: Depurar un control ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuración del contenedor de controles ActiveX [Visual Studio]"
  - "controles ActiveX, depurar"
  - "contenedores, especificar para sesiones de depuración"
  - "controles enlazados a datos, ActiveX"
  - "depurar controles ActiveX"
  - "contenedor de prueba"
  - "probar [Visual Studio], controles ActiveX"
  - "probar [Visual Studio], contenedores de prueba"
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# C&#243;mo: Depurar un control ActiveX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar su configuración, elija la opción Importar y exportar configuraciones del menú Herramientas.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Para depurar el control ActiveX, debe especificar un contenedor \(ejecutable\) en el que ejecutar el control.  
  
### Para especificar un contenedor para la sesión de depuración  
  
1.  En el Explorador de soluciones, seleccione el proyecto.  
  
2.  En el menú **Ver**, elija **Páginas de propiedades**.  
  
3.  En el cuadro de diálogo **Páginas de propiedades del proyecto**, abra la carpeta **Propiedades de configuración** y seleccione **Depuración**.  
  
4.  Debajo de la categoría **Depuración**, busque la propiedad **Comando**.  
  
5.  Especifique el nombre de ruta de acceso para el contenedor.  Por ejemplo, C:\\Archivos de programa\\Internet Explorer\\IEXPLORE.EXE.  
  
6.  Si especifica Internet Explorer como el contenedor y está utilizando Active Desktop, escriba `/new` en el cuadro **Argumentos del comando**.  
  
7.  Haga clic en **Aceptar**.  
  
     Si no especifica ningún contenedor en el cuadro de diálogo **Páginas de propiedades del proyecto**, puede especificarlo al iniciar la depuración.  Cuando se selecciona un comando de ejecución para iniciar la depuración, aparece el [cuadro de diálogo Archivo ejecutable para sesión de depuración](../debugger/executable-for-debugging-session-dialog-box.md).  Especifique el nombre de la ruta de acceso del contenedor en el cuadro de diálogo.  
  
## Vea también  
 [Controles ActiveX](/visual-cpp/mfc/activex-controls)   
 [Probar propiedades y eventos con un contenedor de prueba](/visual-cpp/mfc/testing-properties-and-events-with-test-container)   
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)