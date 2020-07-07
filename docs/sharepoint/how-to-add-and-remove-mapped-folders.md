---
title: 'Cómo: agregar y quitar carpetas asignadas | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 80fbd3e18b8d440eae2873c73013ad7468073640
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014653"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Cómo: agregar y quitar carpetas asignadas
  Algunas carpetas de uso común en SharePoint, como imágenes y diseños, se incrustan profundamente en la jerarquía de archivos. Puede asignar estas carpetas a un proyecto de SharePoint para tener acceso a ellas más fácilmente. Las carpetas asignadas son carpetas del proyecto de SharePoint que corresponden a la ubicación física de los archivos en la instalación de SharePoint Server.

 Cuando se implementa una aplicación de SharePoint, el paquete de solución (. wsp) copia el contenido de la carpeta asignada y todas sus subcarpetas en el servidor que ejecuta SharePoint en la ubicación especificada en el árbol de carpetas de SharePoint. Esta ubicación viene determinada por la propiedad **Ubicación de implementación** que se establece para la carpeta asignada. Cualquier subcarpeta de la carpeta asignada es relativa a la **Ubicación de implementación** de la carpeta asignada. Tenga en cuenta que la propiedad **Ubicación de implementación** , no el nombre de la carpeta asignada, determina dónde se implementan los elementos.
Puede Agregar carpetas asignadas a un proyecto mediante los comandos de la barra de menús o el menú contextual del proyecto. Puede usar la **carpeta asignada agregar "imágenes" de SharePoint** y agregar comandos de la **carpeta "layouts" de SharePoint** para agregar las carpetas asignadas que se usan con más frecuencia. Puede asignar cualquiera de las demás carpetas de SharePoint disponibles al proyecto mediante el comando **Agregar carpeta asignada de SharePoint** en el menú contextual y, a continuación, especificar las carpetas en el cuadro de diálogo **Agregar carpeta asignada de SharePoint** .

## <a name="add-mapped-folders-to-a-project"></a>Agregar carpetas asignadas a un proyecto
 En el procedimiento siguiente se describe cómo agregar dos carpetas asignadas a un proyecto de elemento Web visual. Para empezar, cree un proyecto de elemento Web visual.

#### <a name="to-add-mapped-folders-to-a-project"></a>Para agregar carpetas asignadas a un proyecto

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **Visual Basic** o **Visual C#** , expanda el nodo **Office/SharePoint** y, a continuación, elija el nodo **soluciones de SharePoint** .

3. En la lista de plantillas de proyecto, elija la plantilla de **elemento Web Visual 2013 de SharePoint** .

4. En el cuadro **nombre** , escriba **TestProject1**y elija el botón **Aceptar** .

5. En el **Asistente para la personalización de SharePoint**, elija el botón **Finalizar** para conservar la configuración predeterminada.

6. En **Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**  >  **Agregar carpeta asignada "images" de SharePoint**.

     En el proyecto aparece una carpeta denominada **imágenes** que contiene una subcarpeta denominada TestProject1. Esta carpeta asignada contendrá imágenes para el proyecto de elemento Web visual.

7. En **Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**  >  **Agregar carpeta asignada de SharePoint** para mostrar el cuadro de diálogo **Agregar carpeta asignada de SharePoint** .

8. En la vista de árbol de las carpetas que están disponibles para la asignación, elija la carpeta **recursos** y, a continuación, elija el botón **Aceptar** .

     En el proyecto aparece una carpeta denominada **recursos** . Esta carpeta puede almacenar elementos como archivos de recursos de cadena. Las subcarpetas pueden ser útiles para organizar el contenido de una carpeta asignada, pero no se crean automáticamente cuando se agrega una carpeta asignada mediante el comando **Agregar carpeta asignada de SharePoint** . Para agregar una subcarpeta, elija la carpeta **recursos** y, a continuación, en la barra de menús, elija **proyecto**  >  **nueva carpeta**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Cambiar la ubicación de implementación de una carpeta asignada
 De forma predeterminada, las carpetas asignadas se agregan a ubicaciones específicas en relación con la ruta de instalación raíz de SharePoint, que el token \<SharePointRoot> denota. Sin embargo, puede cambiar esta ubicación cambiando la propiedad **Ubicación de implementación** de la carpeta asignada. Cada carpeta asignada tiene su propia propiedad **Ubicación de implementación** .

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Para cambiar la ubicación de implementación de una carpeta asignada

1. En el proyecto que creó anteriormente, elija una carpeta asignada.

2. En la ventana **propiedades** , elija el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) en la propiedad **Ubicación de implementación** .

3. En el cuadro de diálogo **Agregar carpeta asignada de SharePoint** , vaya a la carpeta a la que desea que apunte la carpeta asignada.

4. Elija el nodo y, a continuación, elija el botón **Aceptar** .

## <a name="rename-or-remove-mapped-folders"></a>Cambiar el nombre o quitar carpetas asignadas

#### <a name="to-rename-or-remove-a-mapped-folder"></a>Para cambiar el nombre o quitar una carpeta asignada

1. En el proyecto que creó anteriormente, elija una carpeta asignada.

2. Para cambiar el nombre de la carpeta asignada, abra el menú contextual, elija **cambiar nombre**, escriba el nuevo nombre y, a continuación, elija la tecla entrar.

     Como alternativa, puede elegir la carpeta asignada cuyo nombre desea cambiar, abrir la ventana **propiedades** y, a continuación, establecer el valor de la propiedad **nombre** de la carpeta en el nuevo nombre.

3. Para quitar una carpeta asignada del proyecto, abra el menú contextual, elija **eliminar**y, a continuación, elija el botón **Aceptar** en el cuadro de diálogo para confirmar la eliminación.

## <a name="see-also"></a>Consulte también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
