---
title: Cuadro de diálogo Selector de URL (desarrollo de SharePoint en Visual Studio) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d8f193e50053b5cdf0b89cf41b09471c513ee9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007957"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Cuadro de diálogo Selector de URL (desarrollo de SharePoint en Visual Studio)
  En el cuadro de diálogo Selector de URL, puede elegir archivos como archivos de página maestra o archivos de imagen que se encuentran en el proyecto o en el servidor local que ejecuta SharePoint.

 Este cuadro de diálogo aparece cuando tiene la opción de elegir un archivo para establecer una propiedad. Puede abrir este cuadro de diálogo eligiendo el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) situado junto a varias propiedades en el **propiedades** ventana. El botón de puntos suspensivos también aparece como un IntelliSense prompt al asignar valores a ciertos atributos en el **origen** la vista del diseñador.

## <a name="uielement-list"></a>Lista de UIElement
 **Las carpetas de proyecto** muestra una lista de las carpetas definidas en el proyecto o en el servidor local que ejecuta SharePoint. Elija el botón de expansión para mostrar las subcarpetas.

 Expanda el **proyecto** nodo para elegir los archivos del proyecto. Para que aparezca como seleccionable en el cuadro de diálogo, los archivos del proyecto deben cumplir los siguientes criterios:

- El archivo debe incluirse en una carpeta asignada.

- El archivo debe agregarse al paquete de solución.

- No se encuentra el archivo en otro proyecto.

  Si desea hacer referencia a archivos que no cumplen estos criterios, deberá especificar la ruta de acceso del archivo manualmente.

  Expanda el **Server** nodo para elegir los archivos que se encuentran en el servidor local que ejecuta SharePoint. Para que aparezca como seleccionable en el cuadro de diálogo, estos archivos deben cumplir los siguientes criterios:

- El archivo debe encontrarse en una de las siguientes carpetas asignadas: **Imágenes**, **diseños**, o **ControlTemplates**.

- No se encuentra el archivo en la base de datos de contenido de SharePoint.

  Si desea hacer referencia a archivos que no cumplen estos criterios, deberá especificar la ruta de acceso del archivo manualmente.

  **Contenido de la carpeta** muestra una lista de archivos en la carpeta seleccionada. Elija un archivo y, a continuación, elija el **Aceptar** botón para cerrar el cuadro de diálogo y enviar su selección al proceso que lo llamó.

  **Archivos de tipo** le permite elegir entre una lista de archivos que son adecuados para la tarea que se va a realizar.

## <a name="see-also"></a>Vea también
- [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
