---
title: "Selector de URL (cuadro de di&#225;logo) (desarrollo de SharePoint en Visual Studio)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.VWD.URLPicker"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, diseñador"
  - "desarrollo de SharePoint en Visual Studio, selector de direcciones URL"
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Selector de URL (cuadro de di&#225;logo) (desarrollo de SharePoint en Visual Studio)
  En el cuadro de diálogo del selector de direcciones URL, puede elegir los archivos como archivos o archivos de imagen de página maestra que se establecen en el proyecto o en el servidor local que ejecuta SharePoint.  
  
 Este cuadro de diálogo aparece cuando tiene la opción de elegir un archivo para establecer una propiedad.  Puede abrir este cuadro de diálogo elija el botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](~/docs/sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")\) situado junto a diversas propiedades en la ventana de **Propiedades** .  El botón de puntos suspensivos también aparece como un mensaje de IntelliSense cuando se asignan valores a ciertos atributos en la vista **Código fuente** del diseñador.  
  
## Lista de UIElement  
 **Carpetas de proyecto**  
 Muestra una lista de las carpetas definidas en el proyecto o en el servidor local que ejecuta SharePoint.  Elija el botón de expansión para mostrar las subcarpetas.  
  
 Expanda el nodo de **Project** para elegir los archivos del proyecto.  Para que aparezcan como elementos seleccionables en el cuadro de diálogo del proyecto, los archivos deben satisfacer los siguientes criterios:  
  
-   El archivo debe estar incluido en una carpeta asignada.  
  
-   El archivo debe agregarse al paquete de la solución.  
  
-   El archivo no puede encontrarse en otro proyecto.  
  
 Si desea hacer referencia a archivos que no cumplen estos criterios, tiene que escribir la ruta de acceso del archivo manualmente.  
  
 Expanda el nodo de **Servidor** para elegir los archivos que se encuentran en el servidor local que ejecuta SharePoint.  Para que aparezcan en el cuadro de diálogo como elementos seleccionables, estos archivos deben satisfacer los siguientes criterios:  
  
-   El archivo debe estar ubicado en una de las siguientes carpetas asignadas: **Images**, **Layouts** o **ControlTemplates**.  
  
-   El archivo no puede encontrarse en la base de datos de contenido de SharePoint.  
  
 Si desea hacer referencia a archivos que no cumplen estos criterios, tiene que escribir la ruta de acceso del archivo manualmente.  
  
 **Contenido de la carpeta**  
 Muestra una lista de los archivos de la carpeta seleccionada.  Elija un archivo, y elija el botón de **Aceptar** para cerrar el cuadro de diálogo y enviar la selección al proceso que lo llamó.  
  
 **Tipo de archivos**  
 Permite elegir entre una lista de archivos adecuado para la tarea que se está realizando.  
  
## Vea también  
 [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Mapa de contenido del entorno de desarrollo web de Visual Studio](http://msdn.microsoft.com/es-es/9c31f93b-c8fb-4599-9b14-6194ec8c7539)  
  
  