---
title: Selector de URL (cuadro de diálogo) (desarrollo de SharePoint)
description: Obtenga información sobre el cuadro de diálogo Selector de URL, que permite al usuario elegir archivos ubicados en su proyecto o en el servidor local que ejecuta SharePoint.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 584b77ab714cb692069fadd6c6fad50e20d46f80
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442539"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>Selector de URL (cuadro de diálogo) (desarrollo de SharePoint en Visual Studio)
  En el cuadro de diálogo Selector de URL, puede elegir archivos como archivos de la página maestra o archivos de imagen que se encuentran en el proyecto o en el servidor local que ejecuta SharePoint.

 Este cuadro de diálogo aparece cuando tiene la opción de elegir un archivo para establecer una propiedad. Para abrir este cuadro de diálogo, puede elegir el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) junto a varias propiedades en la ventana **propiedades** . El botón de puntos suspensivos también aparece como un símbolo del sistema de IntelliSense cuando se asignan valores a ciertos atributos en la vista **código fuente** del diseñador.

## <a name="uielement-list"></a>Lista de UIElement
 **Carpetas de proyecto** Muestra una lista de las carpetas definidas en el proyecto o en el servidor local que ejecuta SharePoint. Elija el botón de expansión para mostrar las subcarpetas.

 Expanda el nodo del **proyecto** para elegir archivos en el proyecto. Para que aparezca como seleccionable en el cuadro de diálogo, los archivos del proyecto deben cumplir los siguientes criterios:

- El archivo debe estar incluido en una carpeta asignada.

- El archivo debe agregarse al paquete de la solución.

- No se puede encontrar el archivo en otro proyecto.

  Si desea hacer referencia a archivos que no cumplen estos criterios, debe escribir la ruta de acceso del archivo manualmente.

  Expanda el nodo del **servidor** para elegir los archivos que se encuentran en el servidor local que ejecuta SharePoint. Para que aparezca como seleccionable en el cuadro de diálogo, estos archivos deben cumplir los siguientes criterios:

- El archivo debe estar ubicado en una de las siguientes carpetas asignadas: **images**, **layouts** o **ControlTemplates**.

- No se puede encontrar el archivo en la base de datos de contenido de SharePoint.

  Si desea hacer referencia a archivos que no cumplen estos criterios, debe escribir la ruta de acceso del archivo manualmente.

  **Contenido de la carpeta** Muestra una lista de los archivos de la carpeta seleccionada. Elija un archivo y, a continuación, elija el botón **Aceptar** para cerrar el cuadro de diálogo y enviar la selección al proceso que lo llamó.

  **Archivos de tipo** Permite elegir entre una lista de archivos adecuados para la tarea que se está llevando a cabo.

## <a name="see-also"></a>Vea también
- [Creación de páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Creación de elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Creación de controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
