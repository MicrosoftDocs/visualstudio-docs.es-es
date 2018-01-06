---
title: "Cuadro de diálogo de selector de URL (desarrollo de SharePoint en Visual Studio) | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c475b44b15b206464e2a910cc410964906706bd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Selector de URL (cuadro de diálogo) (desarrollo de SharePoint en Visual Studio)
  En el cuadro de diálogo Selector de URL, puede elegir archivos como archivos de página maestra o archivos de imagen que se encuentran en el proyecto o en el servidor local que ejecuta SharePoint.  
  
 Este cuadro de diálogo aparece cuando se tiene la opción de elegir un archivo para establecer una propiedad. Puede abrir este cuadro de diálogo seleccionando el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) junto a varias propiedades en la **propiedades** ventana. El botón de puntos suspensivos también aparece como un IntelliSense preguntar al asignar valores a determinados atributos en el **origen** la vista del diseñador.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Carpetas de proyecto**  
 Muestra una lista de las carpetas definidas en el proyecto o en el servidor local que ejecuta SharePoint. Elija el botón de expansión para mostrar las subcarpetas.  
  
 Expanda el **proyecto** nodo para elegir los archivos del proyecto. Para que aparezca como seleccionable en el cuadro de diálogo, los archivos del proyecto deben cumplir los siguientes criterios:  
  
-   El archivo debe estar contenido en una carpeta asignada.  
  
-   El archivo debe agregarse al paquete de solución.  
  
-   El archivo no puede encontrarse en otro proyecto.  
  
 Si desea hacer referencia a archivos que no cumplen estos criterios, tendrá que escribir la ruta de acceso del archivo manualmente.  
  
 Expanda el **Server** nodo para elegir los archivos que se encuentran en el servidor local que ejecuta SharePoint. Para que aparezca como seleccionable en el cuadro de diálogo, estos archivos deben cumplir los siguientes criterios:  
  
-   El archivo debe estar ubicado en una de las siguientes carpetas asignadas: **imágenes**, **diseños**, o **ControlTemplates**.  
  
-   El archivo no puede encontrarse en la base de datos de contenido de SharePoint.  
  
 Si desea hacer referencia a archivos que no cumplen estos criterios, tendrá que escribir la ruta de acceso del archivo manualmente.  
  
 **Contenido de carpeta**  
 Muestra una lista de los archivos de la carpeta seleccionada. Elija un archivo y, a continuación, elija la **Aceptar** botón para cerrar el cuadro de diálogo y enviar su selección al proceso que lo llamó.  
  
 **Archivos de tipo**  
 Permite elegir entre una lista de archivos que son adecuados para la tarea que se va a realizar.  
  
## <a name="see-also"></a>Vea también  
 [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
  