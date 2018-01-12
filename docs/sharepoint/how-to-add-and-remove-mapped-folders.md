---
title: "Cómo: agregar y quitar carpetas asignadas | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 29809344ee8a3f446589ba84f2fc47b1cf407582
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Cómo: Agregar y quitar carpetas asignadas
  Algunas carpetas usadas habitualmente en SharePoint, como imágenes y diseños, profundamente se incrustan en la jerarquía de archivos. Puede asignar estas carpetas en un proyecto de SharePoint para tener acceso a ellos más fácilmente. Las carpetas asignadas son carpetas en el proyecto de SharePoint que corresponden a la ubicación física de los archivos de la instalación del servidor de SharePoint.  
  
 Al implementar una aplicación de SharePoint, el contenido de la carpeta asignada y todas sus subcarpetas se copian por el paquete de solución (.wsp) en el servidor que ejecuta SharePoint en la ubicación especificada en el árbol de carpetas de SharePoint. Esta ubicación viene determinada por la **ubicación de implementación** propiedad que se establece para la carpeta asignada. Todas las subcarpetas de la carpeta asignada son relativo a **ubicación de implementación** de la carpeta asignada. Tenga en cuenta que la **ubicación de implementación** propiedad, no el nombre de la carpeta asignada, determina dónde se implementan los elementos.  
  
 Puede agregar las carpetas asignadas a un proyecto mediante el uso de comandos en la barra de menús o en el menú contextual para el proyecto. Puede usar el **carpeta asignada de SharePoint agregar "Imágenes"** y **agregar SharePoint "Diseños" carpeta** asignan de comandos para agregarlas carpetas que se usan con más frecuencia. Puede asignar cualquiera de las otras carpetas de SharePoint disponibles para el proyecto utilizando la **Agregar carpeta asignada de SharePoint** de comandos en el menú contextual y, a continuación, especificar las carpetas en el **Agregar carpeta asignada de SharePoint** cuadro de diálogo.  
  
## <a name="adding-mapped-folders-to-a-project"></a>Agregar las carpetas asignadas a un proyecto  
 El siguiente procedimiento describe cómo agregar dos carpetas asignadas a un proyecto de elemento web visual. Para empezar, cree un proyecto de elemento web visual.  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>Para agregar las carpetas asignadas a un proyecto  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el **nuevo proyecto** diálogo cuadro, expanda el el **Visual Basic** o **Visual C#** nodo, expanda el **Office/SharePoint** nodo y, a continuación, Elija la **soluciones de SharePoint** nodo.  
  
3.  En la lista de plantillas de proyecto, elija la **elemento Web de SharePoint 2013 Visual** plantilla.  
  
4.  En el **nombre** cuadro, escriba **TestProject1**y, a continuación, elija la **Aceptar** botón.  
  
5.  En el **Asistente para personalización de SharePoint**, elija la **finalizar** botón para conservar la configuración predeterminada.  
  
6.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**, **agregar SharePoint "Imágenes" asignado carpeta**.  
  
     Una carpeta que se denomina **imágenes** aparece en el proyecto y contiene una subcarpeta denominada TestProject1. Esta carpeta asignada contiene imágenes para el proyecto del elemento web visual.  
  
7.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**, **Agregar carpeta asignada de SharePoint** para mostrar el **agregar Carpeta asignada de SharePoint** cuadro de diálogo.  
  
8.  En la vista de árbol de carpetas que están disponibles para la asignación, elija la **recursos** carpeta y, a continuación, elija la **Aceptar** botón.  
  
     Una carpeta que se denomina **recursos** aparece en el proyecto. Esta carpeta puede almacenar los elementos como archivos de recursos de cadena. Las subcarpetas pueden ser útiles para organizar el contenido de una carpeta asignada, pero se crean automáticamente cuando agrega una carpeta asignada mediante el **Agregar carpeta asignada de SharePoint** comando. Para agregar una subcarpeta, elija la **recursos** carpeta y, a continuación, en la barra de menús, elija **proyecto**, **nueva carpeta**.  
  
## <a name="changing-the-deployment-location-of-a-mapped-folder"></a>Cambiar la ubicación de implementación de una carpeta asignada  
 De forma predeterminada, se agregan las carpetas asignadas a ubicaciones específicas en relación con la ruta de instalación raíz de SharePoint, que indica el token {SharePointRoot}. Sin embargo, puede cambiar esta ubicación cambiando el **ubicación de implementación** propiedad de la carpeta asignada. Cada carpeta asignada tiene su propio **ubicación de implementación** propiedad.  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Para cambiar la ubicación de implementación de una carpeta asignada  
  
1.  En el proyecto que creó anteriormente, elija una carpeta asignada.  
  
2.  En el **propiedades** ventana, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) situado en la **implementación ubicación** propiedad.  
  
3.  En el **Agregar carpeta asignada de SharePoint** cuadro de diálogo, busque la carpeta a la que desea que la carpeta asignada para que señale.  
  
4.  Elija el nodo y, a continuación, elija la **Aceptar** botón.  
  
## <a name="renaming-or-removing-mapped-folders"></a>Cambiar el nombre o quitar carpetas asignadas  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>Para cambiar el nombre o quitar una carpeta asignada  
  
1.  En el proyecto que creó anteriormente, elija una carpeta asignada.  
  
2.  Para cambiar el nombre de la carpeta asignada, abra el menú contextual, elija **cambiar el nombre de**, escriba el nuevo nombre y, a continuación, elija la tecla ENTRAR.  
  
     Como alternativa, puede elegir la carpeta asignada que se desea cambiar el nombre, abra el **propiedades** ventana y, a continuación, establezca el valor de la **nombre de la carpeta** propiedad para el nuevo nombre.  
  
3.  Para quitar una carpeta asignada desde el proyecto, abra el menú contextual, elija **eliminar**y, a continuación, elija la **Aceptar** botón en el cuadro de diálogo para confirmar la eliminación.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  