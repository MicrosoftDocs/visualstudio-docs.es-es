---
title: 'Cómo: agregar y quitar ensamblados adicionales | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 07b9016a4e246d3ed5a2697d924f556517a8226f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014824"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Cómo: agregar y quitar ensamblados adicionales
  Si un paquete de SharePoint depende de otros ensamblados para la funcionalidad o los datos, puede agregar esos ensamblados al paquete de solución (.wsp). De esta manera, el servidor de SharePoint se asegura de que los ensamblados personalizados se instalan con un paquete.

 También puede agregar y cambiar los controles seguros y los archivos de recursos de clase asociados a los ensamblados.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Agregar ensamblados adicionales, controles seguros y recursos de clase
 Puede agregar ensamblados adicionales al paquete de solución de SharePoint. Los ensamblados adicionales de una solución en espacio aislado se implementan en la memoria caché global de ensamblados, pero los elementos de proyecto de SharePoint incluidos en una solución en espacio aislado se agregan a la base de datos de contenido. También puede agregar controles seguros y recursos de clase a estos ensamblados adicionales. Para obtener más información sobre los controles seguros, vea [proporcionar información de empaquetado e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) o "crear una entrada de SafeControl" en [implementar elementos Web en SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

#### <a name="to-add-an-existing-assembly"></a>Para agregar un ensamblado existente

1. Abra el **Diseñador de paquetes**. Para obtener más información, vea [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Elija la pestaña **Opciones avanzadas**.

3. Elija el botón **Agregar** y, a continuación, elija **Agregar ensamblado existente** en la lista.

     Aparecerá el cuadro de diálogo **Agregar ensamblado existente** .

4. Elija los puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) y, a continuación, elija el ensamblado que desea agregar. Por motivos de portabilidad, se recomienda utilizar una ruta de acceso relativa al ensamblado seleccionado.

5. Para el **destino de implementación**, elija el botón de opción **GlobalAssemblyCache** para implementar el ensamblado en la caché global de ensamblados o elija el botón de opción **WebApplication** para implementar el ensamblado en la carpeta WebApplication en el servidor que ejecuta SharePoint.

#### <a name="to-add-an-assembly-from-project-output"></a>Para agregar un ensamblado desde la salida del proyecto

1. Abra el **Diseñador de paquetes**.

     Para obtener más información, vea [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Elija la pestaña **Opciones avanzadas**.

3. Elija el botón **Agregar** y, a continuación, elija **Agregar ensamblado desde la salida del proyecto** en la lista.

     Aparecerá el cuadro **de diálogo Agregar ensamblado desde la salida del proyecto** .

4. En la lista **proyecto de origen** , elija el proyecto de origen que desea agregar.

5. Para el **destino de implementación**, elija el botón de opción **GlobalAssemblyCache** para implementar el ensamblado en la caché global de ensamblados o elija el botón de opción **WebApplication** para implementar el ensamblado en la carpeta WebApplication en el servidor que ejecuta SharePoint.

#### <a name="to-add-a-safe-control"></a>Para agregar un control seguro

1. Abra el cuadro de diálogo **Editar ensamblado existente** . Para ello, abra el diseñador de paquetes, elija la pestaña **Opciones avanzadas** , seleccione un ensamblado y, a continuación, elija el botón **Editar** .

2. En el panel **controles seguros** , elija el botón **haga clic aquí para agregar un nuevo elemento** .

3. En la columna **nombre de ensamblado** , escriba el nombre del ensamblado.

4. En la columna **espacio de nombres** , escriba el nombre del espacio de nombres para el control seguro.

5. En la columna **nombre de tipo** , escriba el nombre del tipo.

#### <a name="to-add-a-class-resource"></a>Para agregar un recurso de clase

1. Abra el cuadro de diálogo **Editar ensamblado existente** . Para ello, abra el diseñador de paquetes, elija la pestaña **Opciones avanzadas** , seleccione un ensamblado y, a continuación, elija el botón **Editar** .

2. En el panel **recursos de clase** , elija el botón **haga clic aquí para agregar un nuevo elemento** .

3. En la columna **nombre de archivo** , elija los puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) y elija el recurso de clase que desee agregar.

## <a name="delete-custom-assemblies"></a>Eliminar ensamblados personalizados
 Puede eliminar los ensamblados de un paquete de SharePoint o eliminar los controles seguros y los recursos de clase de los ensamblados existentes.

#### <a name="to-delete-an-existing-assembly"></a>Para eliminar un ensamblado existente

1. Abra el **Diseñador de paquetes**. Para obtener más información, vea [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Elija la pestaña **Opciones avanzadas**.

3. En el panel **ensamblados adicionales** , elija el ensamblado personalizado que desea eliminar.

4. Elija el botón **Eliminar**.

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Para eliminar un control seguro de un ensamblado

1. Abra el cuadro de diálogo **Editar ensamblado existente** . Para ello, abra el diseñador de paquetes, elija la pestaña **Opciones avanzadas** , seleccione un ensamblado y, a continuación, elija el botón **Editar** .

2. Elija el control seguro que desee eliminar.

3. Elija la tecla Supr.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Para eliminar un recurso de clase de un ensamblado

1. Abra el cuadro de diálogo **Editar ensamblado existente** . Para ello, abra el diseñador de paquetes, elija la pestaña **Opciones avanzadas** , seleccione un ensamblado y, a continuación, elija el botón **Editar** .

2. Elija el recurso de clase que desee eliminar.

3. Elija la tecla Supr.

## <a name="see-also"></a>Consulte también
- [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Cómo: agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
