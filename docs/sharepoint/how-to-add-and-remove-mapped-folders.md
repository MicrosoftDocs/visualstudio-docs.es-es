---
title: Filtrar Agregar y quitar carpetas asignadas | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21ecf370134558d7b47faad1c215fa9a65019316
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646218"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Cómo: agregar y quitar carpetas asignadas
  Algunas carpetas usadas habitualmente en SharePoint, como imágenes y diseños, está profundamente integrado en la jerarquía de archivos. Puede asignar estas carpetas en un proyecto de SharePoint para tener acceso a ellos más fácilmente. Carpetas asignadas son carpetas en el proyecto de SharePoint que corresponden a la ubicación física de los archivos de la instalación del servidor de SharePoint.

 Al implementar una aplicación de SharePoint, el contenido de la carpeta asignada y todas sus subcarpetas se copian por el paquete de solución (.wsp) en el servidor que ejecuta SharePoint en la ubicación especificada en el árbol de carpetas de SharePoint. Esta ubicación viene determinada por la **ubicación de implementación** propiedad que se establece para la carpeta asignada. Todas las subcarpetas de la carpeta asignada son relativas a **ubicación de implementación** de la carpeta asignada. Tenga en cuenta que el **ubicación de implementación** propiedad, no el nombre de la carpeta asignada, determina dónde se implementan los elementos.
Puede agregar carpetas asignadas a un proyecto mediante el uso de comandos en la barra de menús o en el menú contextual del proyecto. Puede usar el **carpeta asignada de SharePoint agregar "Imágenes"** y **agregar SharePoint "Diseños" carpeta** comandos para agregar estos elementos asignan las carpetas que se usan con mayor frecuencia. Puede asignar cualquiera de las otras carpetas de SharePoint disponibles para el proyecto mediante el uso de la **Agregar carpeta asignada de SharePoint** comando en el menú contextual y, a continuación, especificar las carpetas en el **Agregar carpeta asignada de SharePoint** cuadro de diálogo.

## <a name="add-mapped-folders-to-a-project"></a>Agregar carpetas asignadas a un proyecto
 El siguiente procedimiento describe cómo agregar dos carpetas asignadas a un proyecto de elemento web visual. Para empezar, cree un proyecto de elemento web visual.

#### <a name="to-add-mapped-folders-to-a-project"></a>Para agregar carpetas asignadas a un proyecto

1.  En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2.  En el **nuevo proyecto** diálogo cuadro, expanda el el **Visual Basic** o **Visual C#** nodo, expanda el **Office/SharePoint** nodo y, a continuación, Elija la **soluciones de SharePoint** nodo.

3.  En la lista de plantillas de proyecto, elija el **elemento Web de SharePoint 2013 Visual** plantilla.

4.  En el **nombre** , escriba **TestProject1**y, a continuación, elija el **Aceptar** botón.

5.  En el **Asistente de personalización de SharePoint**, elija el **finalizar** botón para conservar la configuración predeterminada.

6.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto** > **carpeta asignada de SharePoint agregar "Imágenes"**.

     Una carpeta que se denomina **imágenes** aparece en el proyecto y contiene una subcarpeta denominada TestProject1. Esta carpeta asignada contiene imágenes para el proyecto de elemento web visual.

7.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto** > **Agregar carpeta asignada de SharePoint** para mostrar el  **Agregar carpeta asignada de SharePoint** cuadro de diálogo.

8.  En la vista de árbol de carpetas que están disponibles para la asignación, elija el **recursos** carpeta y, a continuación, elija el **Aceptar** botón.

     Una carpeta que se denomina **recursos** aparece en el proyecto. Esta carpeta puede almacenar elementos como archivos de recursos de cadena. Las subcarpetas pueden ser útiles para organizar el contenido de una carpeta asignada, pero se crean automáticamente cuando agrega una carpeta asignada mediante el **Agregar carpeta asignada de SharePoint** comando. Para agregar una subcarpeta, elija el **recursos** carpeta y, a continuación, en la barra de menús, elija **proyecto** > **nueva carpeta**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Cambiar la ubicación de implementación de una carpeta asignada
 De forma predeterminada, se agregan carpetas asignadas a ubicaciones específicas en relación con la ruta de instalación raíz de SharePoint, que el token \<SharePointRoot > denota. Sin embargo, puede cambiar esta ubicación cambiando el **ubicación de implementación** propiedad de la carpeta asignada. Cada carpeta asignada tiene su propio **ubicación de implementación** propiedad.

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Para cambiar la ubicación de implementación de una carpeta asignada

1.  En el proyecto que creó anteriormente, elija una carpeta asignada.

2.  En el **propiedades** ventana, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) situado en la **implementación ubicación** propiedad.

3.  En el **Agregar carpeta asignada de SharePoint** cuadro de diálogo, vaya a la carpeta a la que desea que la carpeta asignada para que señale.

4.  Elija el nodo y, a continuación, elija el **Aceptar** botón.

## <a name="rename-or-remove-mapped-folders"></a>Cambiar el nombre o quitar carpetas asignadas

#### <a name="to-rename-or-remove-a-mapped-folder"></a>Para cambiar el nombre o quitar una carpeta asignada

1.  En el proyecto que creó anteriormente, elija una carpeta asignada.

2.  Para cambiar el nombre de la carpeta asignada, abra el menú contextual, elija **cambiar el nombre**, escriba el nuevo nombre y, a continuación, elija la tecla ENTRAR.

     Como alternativa, puede elegir la carpeta asignada que se desea cambiar el nombre, abra el **propiedades** ventana y, a continuación, establezca el valor de la **nombre de la carpeta** propiedad para el nuevo nombre.

3.  Para quitar una carpeta asignada desde el proyecto, abra el menú contextual, elija **eliminar**y, a continuación, elija el **Aceptar** botón en el cuadro de diálogo para confirmar la eliminación.

## <a name="see-also"></a>Vea también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
