---
title: Procedimiento Agregar y quitar ensamblados adicionales | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e9653fe6ab79e3615ecb231d19dd9ee20133faf6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887015"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Procedimiento Agregar y quitar ensamblados adicionales
  Si un paquete de SharePoint depende de otros ensamblados para la funcionalidad o los datos, puede agregar esos ensamblados al paquete de solución (.wsp). De esta manera, el servidor de SharePoint se asegura de que los ensamblados personalizados se instalan con un paquete.  
  
 También puede agregar y cambiar los controles seguros y los archivos de recursos de clase asociados a los ensamblados.  
  
## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Agregar ensamblados adicionales, los controles seguros y recursos de clase  
 Puede agregar ensamblados adicionales al paquete de solución de SharePoint. Los ensamblados adicionales de una solución en espacio aislado se implementan en la memoria caché global de ensamblados, pero los elementos de proyecto de SharePoint incluidos en una solución en espacio aislado se agregan a la base de datos de contenido. También puede agregar controles seguros y recursos de clase a estos ensamblados adicionales. Para obtener más información sobre los controles seguros, vea [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) o "Creación de una entrada SafeControl" en [implementar elementos Web en SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>Para agregar un ensamblado existente  
  
1.  Abra el **diseñador del paquete**. Para obtener más información, vea [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Elija la **avanzadas** ficha.  
  
3.  Elija la **agregar** botón y, a continuación, elija **Agregar ensamblado existente** en la lista.  
  
     El **Agregar ensamblado existente** aparece el cuadro de diálogo.  
  
4.  Elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) y, a continuación, elija el ensamblado que desea agregar. Por motivos de portabilidad, se recomienda utilizar una ruta de acceso relativa al ensamblado seleccionado.  
  
5.  Para el **destino de implementación**, elija el **GlobalAssemblyCache** botón de opción para implementar el ensamblado en la caché global de ensamblados o elija el **WebApplication** opción botón para implementar el ensamblado en la carpeta WebApplication del servidor que ejecuta SharePoint.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>Para agregar un ensamblado desde la salida del proyecto  
  
1.  Abra el **diseñador del paquete**.  
  
     Para obtener más información, vea [Cómo: Personalizar un paquete de solución SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Elija la **avanzadas** ficha.  
  
3.  Elija la **agregar** botón y, a continuación, elija **Agregar ensamblado desde la salida del proyecto** en la lista.  
  
     El **Agregar ensamblado desde la salida del proyecto** aparece el cuadro de diálogo.  
  
4.  En el **proyecto de código fuente** lista y elija el proyecto de origen que desea agregar.  
  
5.  Para el **destino de implementación**, elija el **GlobalAssemblyCache** botón de opción para implementar el ensamblado en la caché global de ensamblados o elija el **WebApplication** opción botón para implementar el ensamblado en la carpeta WebApplication del servidor que ejecuta SharePoint.  
  
#### <a name="to-add-a-safe-control"></a>Para agregar un control seguro  
  
1.  Abra el **Editar ensamblado existente** cuadro de diálogo. Para ello, abra el Diseñador de paquetes, elija el **avanzadas** ficha, elija un ensamblado y, a continuación, elija el **editar** botón.  
  
2.  En el **controles seguros** panel, elija el **haga clic aquí para agregar un nuevo elemento** botón.  
  
3.  En el **nombre del ensamblado** columna, escriba el nombre del ensamblado.  
  
4.  En el **Namespace** columna, escriba el nombre del espacio de nombres para el control seguro.  
  
5.  En el **nombre de tipo** columna, escriba el nombre del tipo.  
  
#### <a name="to-add-a-class-resource"></a>Para agregar un recurso de clase  
  
1.  Abra el **Editar ensamblado existente** cuadro de diálogo. Para ello, abra el Diseñador de paquetes, elija el **avanzadas** ficha, elija un ensamblado y, a continuación, elija el **editar** botón.  
  
2.  En el **recursos de clase** panel, elija el **haga clic aquí para agregar un nuevo elemento** botón.  
  
3.  En el **nombre de archivo** columna, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) y elija el recurso de clase que desea agregar.  
  
## <a name="delete-custom-assemblies"></a>Eliminar ensamblados personalizados  
 Puede eliminar los ensamblados de un paquete de SharePoint o eliminar los controles seguros y los recursos de clase de los ensamblados existentes.  
  
#### <a name="to-delete-an-existing-assembly"></a>Para eliminar un ensamblado existente  
  
1.  Abra el **diseñador del paquete**. Para obtener más información, vea [Cómo: Personalizar un paquete de solución SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Elija la **avanzadas** ficha.  
  
3.  En el **ensamblados adicionales** panel, elija el ensamblado personalizado que desea eliminar.  
  
4.  Elija la **eliminar** botón.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Para eliminar un control seguro de un ensamblado  
  
1.  Abra el **Editar ensamblado existente** cuadro de diálogo. Para ello, abra el Diseñador de paquetes, elija el **avanzadas** ficha, elija un ensamblado y, a continuación, elija el **editar** botón.  
  
2.  Elija el control seguro que desee eliminar.  
  
3.  Elija la tecla Supr.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Para eliminar un recurso de clase de un ensamblado  
  
1.  Abra el **Editar ensamblado existente** cuadro de diálogo. Para ello, abra el Diseñador de paquetes, elija el **avanzadas** ficha, elija un ensamblado y, a continuación, elija el **editar** botón.  
  
2.  Elija el recurso de clase que desee eliminar.  
  
3.  Elija la tecla Supr.  
  
## <a name="see-also"></a>Vea también
 [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
