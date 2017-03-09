---
title: "Creaci&#243;n de una ventana de herramientas b&#225;sica | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SDK de Visual Studio, ventanas de herramientas"
  - "ventanas de herramientas, crear en IDE"
ms.assetid: 1e96cf07-bde4-445b-bcd0-48cadb351dde
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Creaci&#243;n de una ventana de herramientas b&#225;sica
Las ventanas de herramientas son comunes en Visual Studio: las ventanas **Explorador de soluciones**, **Lista de tareas**, **Lista de errores** y **Salida** son todas las ventanas de herramientas. Todas las ventanas de herramientas se pueden acoplar en el IDE de la misma manera. El acoplamiento de predicción permite a los usuarios administrar las tareas y la información de manera eficaz.  
  
 La plantilla de paquete de Visual Studio crea una implementación básica de una ventana de herramientas simple.  
  
### Para crear una ventana de herramientas mediante la plantilla de paquete de Visual Studio  
  
1.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda **Otros tipos de proyectos** y, después, haga clic en **Extensibilidad**.  
  
3.  En el panel **Plantillas**, haga clic en **Paquete de Visual Studio**.  
  
4.  En el cuadro **Ubicación**, escriba la ruta de acceso de archivo del VSPackage.  
  
5.  En el cuadro **Nombre**, escriba el nombre de la solución y haga clic en **Aceptar** para iniciar la plantilla.  
  
6.  En la página **Seleccione un lenguaje de programación**, seleccione C\# o Visual Basic. Haga que la plantilla genere un archivo key.snk para firmar el ensamblado. Como alternativa, haga clic en **Examinar** para buscar su propio archivo de clave. La plantilla crea una copia del archivo de clave y le asigna el nombre key.snk.  
  
7.  En la página **Información básica del paquete de VS**, especifique los detalles del paquete de VS o acepte los predeterminados. Para obtener más información, consulta [Tutorial: Crear un comando de menú mediante la plantilla de paquete de Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
8.  En la página **Seleccionar opciones del paquete de VS**, active Ventana de herramientas.  
  
9. En la página Opciones de la ventana de herramientas, escriba el nombre de la barra de título en el cuadro **Nombre de ventana**. Este nombre también se usa como texto para mostrar del comando de menú de la ventana de herramientas. El comando de menú se agrega al submenú **Otras ventanas** del menú **Ver**. Escriba el identificador de comando de la ventana de herramientas en el cuadro **Identificador de comando** o acepte el valor predeterminado.  
  
10. Haga clic en **Finalizar** para crear el VSPackage en la carpeta que especificó.  
  
### Para probar la ventana de herramientas  
  
1.  En el menú **Ver**, elija **Otras ventanas** y, después, haga clic en el comando de la ventana de herramientas. Aparece una ventana de herramientas con un botón **Click Me\!**.  
  
2.  Haga clic en el botón. Aparece un mensaje con el texto:  
  
     We are inside \[Company.\<VSPackage name\>.MyControl\].button1\_Click\(\).  
  
## Vea también  
 [Abrir una ventana de herramientas mediante programación](../misc/opening-a-tool-window-programmatically.md)   
 [Elementos fundamentales de VSPackage](../misc/vspackage-essentials.md)