---
title: 'Cómo: Agregar y quitar carpetas asignadas | Microsoft Docs'
description: Agregar y quitar carpetas asignadas a un proyecto en SharePoint.  Cambie la ubicación de implementación de una carpeta asignada. Cambie el nombre o quite las carpetas asignadas.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a9b74ba786c9d1104fd507442d959e75afb17bf2
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112426"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Cómo: Agregar y quitar carpetas asignadas

  Algunas carpetas usadas habitualmente en SharePoint, como Imágenes y diseños, están profundamente incrustadas en la jerarquía de archivos. Puede asignar estas carpetas a un proyecto de SharePoint para acceder a ellas más fácilmente. Las carpetas asignadas son carpetas del proyecto de SharePoint que corresponden a la ubicación física de los archivos en la instalación de SharePoint Server.

 Al implementar una aplicación de SharePoint, el paquete de solución (.wsp) copia el contenido de la carpeta asignada y todas sus subcarpetas en el servidor que ejecuta SharePoint en la ubicación especificada en el árbol de carpetas de SharePoint. Esta ubicación viene determinada por la **propiedad Ubicación de** implementación que se establece para la carpeta asignada. Las subcarpetas de la carpeta asignada son relativas a **la ubicación de implementación** de la carpeta asignada. Tenga en cuenta **que la propiedad Ubicación** de implementación, no el nombre de la carpeta asignada, determina dónde se implementan los elementos.
Puede agregar carpetas asignadas a un proyecto mediante comandos en la barra de menús o en el menú contextual del proyecto. Puede usar los comandos agregar carpeta asignada **"Imágenes"** de SharePoint y Agregar carpeta **de "diseños"** de SharePoint para agregar las carpetas asignadas que se usan con más frecuencia. Puede asignar cualquiera de las demás carpetas de SharePoint disponibles al proyecto mediante el comando Agregar carpeta asignada de **SharePoint** en el menú contextual y, a continuación, especificar las carpetas en el cuadro de diálogo Agregar carpeta asignada de **SharePoint** .

## <a name="add-mapped-folders-to-a-project"></a>Agregar carpetas asignadas a un proyecto

 En el procedimiento siguiente se describe cómo agregar dos carpetas asignadas a un proyecto de elemento web visual. Para empezar, cree un proyecto de elemento web visual.

## <a name="to-add-mapped-folders-to-a-project"></a>Para agregar carpetas asignadas a un proyecto

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.
::: moniker range="=vs-2017"
2. En el **cuadro de diálogo** Nuevo proyecto, expanda el nodo **Visual Basic** o **Visual C#,** expanda el nodo **Office/SharePoint** y, a continuación, elija el **nodo Soluciones de SharePoint.**

3. En la lista de plantillas de proyecto, elija la plantilla **Elemento web visual de SharePoint 2013.**

4. En el **cuadro Nombre,** escriba **TestProject1** y elija el **botón** Aceptar.
::: moniker-end
::: moniker range=">=vs-2019"
2. En el **cuadro de diálogo Crear un nuevo** proyecto, seleccione el elemento web visual de *SharePoint** para la versión concreta de SharePoint que ha instalado. Por ejemplo, si tiene instalación de SharePoint 2019, seleccione la plantilla Elemento **web visual de SharePoint 2019.**
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. En el **cuadro Nombre,** escriba **TestProject1.**
4. A continuación, **elija el botón** Crear.
::: moniker-end

5. En el **Asistente para personalización de SharePoint,** elija **el botón Finalizar** para conservar la configuración predeterminada.

6. En **Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija Proyecto Agregar carpeta asignada  >  **"Imágenes" de SharePoint**.

     Una carpeta denominada **Images** aparece en el proyecto y contiene una subcarpeta denominada TestProject1. Esta carpeta asignada contendrá imágenes para el proyecto de elemento web visual.

7. En **Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija Proyecto Agregar carpeta asignada de SharePoint para mostrar el cuadro de diálogo Agregar carpeta  >   asignada de **SharePoint** .

8. En la vista de árbol de las carpetas que están disponibles para la asignación, elija la carpeta **Recursos** y, a continuación, elija **el botón** Aceptar.

     Aparece una carpeta denominada **Recursos** en el proyecto. Esta carpeta puede almacenar elementos como archivos de recursos de cadena. Las subcarpetas pueden ser útiles para organizar el contenido de una carpeta asignada, pero no se crean automáticamente al agregar una carpeta asignada mediante el comando Agregar carpeta asignada de **SharePoint.** Para agregar una carpeta, elija la carpeta **Recursos** y, a continuación, en la barra de menús, elija **Project**  >  **New Folder (Proyecto nueva carpeta).**

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Cambiar la ubicación de implementación de una carpeta asignada

 De forma predeterminada, las carpetas asignadas se agregan a ubicaciones específicas relativas a la ruta de instalación raíz de SharePoint, que el token \<SharePointRoot> denota. Sin embargo, puede cambiar esta ubicación cambiando la **propiedad Ubicación de** implementación de la carpeta asignada. Cada carpeta asignada tiene su propia propiedad **Ubicación de** implementación.

### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Para cambiar la ubicación de implementación de una carpeta asignada

1. En el proyecto que creó anteriormente, elija una carpeta asignada.

2. En la **ventana Propiedades,** elija el botón de puntos suspensivos ![(ASP.NET de puntos](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")suspensivos del Diseñador móvil) de la propiedad Ubicación **de** implementación.

3. En el cuadro de diálogo Agregar carpeta asignada de **SharePoint,** vaya a la carpeta a la que desea que apunte la carpeta asignada.

4. Elija el nodo y, a continuación, elija **el botón** Aceptar.

## <a name="rename-or-remove-mapped-folders"></a>Cambiar el nombre o quitar carpetas asignadas

### <a name="to-rename-or-remove-a-mapped-folder"></a>Para cambiar el nombre o quitar una carpeta asignada

1. En el proyecto que creó anteriormente, elija una carpeta asignada.

2. Para cambiar el nombre de la carpeta asignada, abra su menú contextual, elija **Cambiar** nombre, escriba el nuevo nombre y, a continuación, elija la tecla Entrar.

     Como alternativa, puede elegir la carpeta asignada cuyo nombre  desea cambiar, abrir la ventana  Propiedades y, a continuación, establecer el valor de la propiedad Nombre de carpeta en el nuevo nombre.

3. Para quitar una carpeta asignada del proyecto, abra su menú contextual, elija Eliminar y, a continuación, elija el botón Aceptar del cuadro de diálogo para confirmar la eliminación. 

## <a name="see-also"></a>Consulte también

- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
