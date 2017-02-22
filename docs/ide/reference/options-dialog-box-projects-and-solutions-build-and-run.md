---
title: "Cuadro de di&#225;logo Opciones, Proyectos y soluciones, Compilar y ejecutar | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.Build_and_Run"
  - "VS.ToolsOptionsPag.Projects.Build_and_Run"
helpviewer_keywords: 
  - "compilaciones [Visual Studio], configurar"
  - "ejecutar acciones"
  - "depurador, opciones de ejecución"
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Cuadro de di&#225;logo Opciones, Proyectos y soluciones, Compilar y ejecutar
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En este cuadro de diálogo puede especificar el número máximo de proyectos de Visual C\+\+ o Visual C\# que se pueden compilar al mismo tiempo, determinados comportamientos de compilación predeterminados y algunos ajustes de registro de compilación.  Para abrir el cuadro de diálogo **Opciones**, seleccione **Herramientas**, **Opciones** en la barra de menús.  Para acceder a este conjunto de opciones, expanda **Proyectos y soluciones** y, a continuación, elija **Compilar y ejecutar**.  
  
## Lista de UIElement  
 **Número máximo de compilaciones de proyecto paralelas**  
 Especifica el número máximo de proyectos de Visual C\+\+ y Visual C\# que se pueden compilar al mismo tiempo.  Para optimizar el proceso de compilación, el número máximo de compilaciones de proyecto paralelas se establece automáticamente en el número de CPU que tenga el equipo.  El máximo es 32.  
  
 **Compilar proyectos de inicio y dependencias únicamente al ejecutar**  
 Si selecciona esta casilla al presionar la tecla F5, solo se compila el proyecto de inicio y sus dependencias. Elija **Depurar**, **Iniciar** en la barra de menús o elija **Compilar**, **Compilar** en la barra de menús.  Si se anula la selección de esta casilla al presionar la tecla F5, se compilan todos los proyectos, dependencias y archivos de la solución. Elija **Depurar**, **Iniciar** en la barra de menús o elija **Compilar**, **Compilar** en la barra de menús.  Esta opción se encuentra desactivada de forma predeterminada.  
  
 **Al ejecutar, cuando los proyectos no estén actualizados**  
 > [!NOTE]
>  Esta lista solo se aplica a proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 De forma predeterminada, aparece un mensaje si una configuración de proyecto no está actualizada al presionar la tecla F5 o elegir **Depurar**, **Iniciar** en la barra de menús.  Puede especificar si se debe compilar el proyecto de todos modos y si aparece el mensaje.  Utilice esta opción para especificar si aparece el mensaje y cuál debería ser el comportamiento de compilación en caso de que no aparezca el mensaje.  
  
 **Compilar siempre**  
 No aparece el cuadro de mensaje y se compila el proyecto a pesar de que la configuración no está actualizada.  Esta opción se establece cuando se selecciona la casilla **No volver a mostrar este cuadro de diálogo** y, a continuación, se elige el botón **Sí**.  
  
 **No compilar nunca**  
 No aparece el cuadro de mensaje y no se compila el proyecto.  Esta opción se establece cuando se selecciona la casilla **No volver a mostrar este cuadro de diálogo** y, a continuación, se elige el botón **No**.  
  
 **Preguntar si se compila**  
 Muestra el cuadro de mensaje cada vez que una configuración de proyecto no está actualizada.  
  
 **En ejecución, cuando se produzcan errores de compilación o implementación**  
 Si se producen errores de compilación al iniciar una compilación desde el menú **Compilar**, aparece un mensaje.  Puede especificar si desea proceder a iniciar la aplicación y si aparece el mensaje cada vez que se producen errores de compilación.  Utilice esta opción para especificar si aparece el mensaje y cuál debería ser el comportamiento en caso de que no aparezca el mensaje.  
  
> [!NOTE]
>  Esta opción solo es aplicable a proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 **Preguntar al iniciar**  
 Muestra un cuadro de mensaje cada vez que se producen errores de compilación.  
  
 **No iniciar**  
 No aparece el cuadro de mensaje y no se inicia la aplicación.  Esta opción se establece cuando se selecciona la casilla **No volver a mostrar este cuadro de diálogo** y, a continuación, se elige el botón **No**.  
  
 **Iniciar versión antigua**  
 No aparece el cuadro de mensaje y no se inicia la versión recién compilada de la aplicación.  Esta opción se establece cuando se selecciona la casilla **No volver a mostrar este cuadro de diálogo** y, a continuación, se elige el botón **Sí**.  
  
 **Para soluciones nuevas, use el proyecto seleccionado actualmente como proyecto de inicio**  
 Si se selecciona esta casilla, las nuevas soluciones utilizan el proyecto seleccionado actualmente como proyecto de inicio.  
  
 **Contenido de los resultados de compilación del proyecto de MSBuild**  
 Determina cuánta información aparece en la ventana de **salida** de la compilación.  
  
 **Contenido del archivo de registro de compilación del proyecto de MSBuild**  
 > [!NOTE]
>  Esta opción solo es aplicable a proyectos de Visual C\+\+.  
  
 Determina cuánta información se escribe en el archivo de registro de compilación, que se encuentra en \\...  \\*ProjectName*\\Debug\\*ProjectName*.log.  
  
## Vea también  
 [Compilar aplicaciones en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)