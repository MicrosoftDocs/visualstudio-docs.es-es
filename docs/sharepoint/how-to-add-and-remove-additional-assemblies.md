---
title: "Cómo: agregar y quitar ensamblados adicionales | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 13ea5388a7b4ce2d1a045dec6339dc59e5c68393
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Cómo: Agregar y quitar ensamblados adicionales
  Si un paquete de SharePoint depende de otros ensamblados para la funcionalidad o los datos, puede agregar esos ensamblados al paquete de solución (.wsp). De esta manera, el servidor de SharePoint se asegura de que los ensamblados personalizados se instalan con un paquete.  
  
 También puede agregar y cambiar los controles seguros y los archivos de recursos de clase asociados a los ensamblados.  
  
## <a name="adding-additional-assemblies-safe-controls-and-class-resources"></a>Agregar ensamblados, controles seguros y recursos de clase adicionales  
 Puede agregar ensamblados adicionales al paquete de solución de SharePoint. Los ensamblados adicionales de una solución en espacio aislado se implementan en la memoria caché global de ensamblados, pero los elementos de proyecto de SharePoint incluidos en una solución en espacio aislado se agregan a la base de datos de contenido. También puede agregar controles seguros y recursos de clase a estos ensamblados adicionales. Para obtener más información acerca de controles seguros, vea [proporcionando información empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) o "Crear una entrada SafeControl" en [implementar elementos Web en SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>Para agregar un ensamblado existente  
  
1.  Abra la **diseñador del paquete**. Para obtener más información, consulte [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Elija la **avanzadas** ficha.  
  
3.  Elija la **agregar** botón y, a continuación, elija **Agregar ensamblado existente** en la lista.  
  
     El **Agregar ensamblado existente** aparece el cuadro de diálogo.  
  
4.  Elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) y, a continuación, elija el ensamblado que se va a agregar. Por motivos de portabilidad, se recomienda utilizar una ruta de acceso relativa al ensamblado seleccionado.  
  
5.  Para el **destino de implementación**, elija la **GlobalAssemblyCache** botón de opción para implementar el ensamblado en la caché global de ensamblados o elija la **WebApplication** opción botón para implementar el ensamblado en la carpeta WebApplication del servidor que ejecuta SharePoint.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>Para agregar un ensamblado desde la salida del proyecto  
  
1.  Abra la **diseñador del paquete**.  
  
     Para obtener más información, consulte [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Elija la **avanzadas** ficha.  
  
3.  Elija la **agregar** botón y, a continuación, elija **Agregar ensamblado desde la salida del proyecto** en la lista.  
  
     El **Agregar ensamblado desde la salida del proyecto** aparece el cuadro de diálogo.  
  
4.  En el **proyecto de código fuente** lista y elija el proyecto de origen que desea agregar.  
  
5.  Para el **destino de implementación**, elija la **GlobalAssemblyCache** botón de opción para implementar el ensamblado en la caché global de ensamblados o elija la **WebApplication** opción botón para implementar el ensamblado en la carpeta WebApplication del servidor que ejecuta SharePoint.  
  
#### <a name="to-add-a-safe-control"></a>Para agregar un control seguro  
  
1.  Abra la **Editar ensamblado existente** cuadro de diálogo. Para ello, abra el Diseñador de paquetes, elija la **avanzadas** ficha, elija un ensamblado y, a continuación, elija la **editar**botón.  
  
2.  En el **controles seguros** panel, elija la **haga clic aquí para agregar un nuevo elemento** botón.  
  
3.  En el **nombre de ensamblado** columna, escriba el nombre del ensamblado.  
  
4.  En el **Namespace** columna, escriba el nombre del espacio de nombres para el control seguro.  
  
5.  En el **nombre de tipo** columna, escriba el nombre del tipo.  
  
#### <a name="to-add-a-class-resource"></a>Para agregar un recurso de clase  
  
1.  Abra la **Editar ensamblado existente** cuadro de diálogo. Para ello, abra el Diseñador de paquetes, elija la **avanzadas** ficha, elija un ensamblado y, a continuación, elija la **editar** botón.  
  
2.  En el **recursos de clase** panel, elija la **haga clic aquí para agregar un nuevo elemento** botón.  
  
3.  En el **nombre de archivo** columna, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) y elija el recurso de clase que se va a agregar.  
  
## <a name="deleting-custom-assemblies"></a>Eliminar ensamblados personalizados  
 Puede eliminar los ensamblados de un paquete de SharePoint o eliminar los controles seguros y los recursos de clase de los ensamblados existentes.  
  
#### <a name="to-delete-an-existing-assembly"></a>Para eliminar un ensamblado existente  
  
1.  Abra la **diseñador del paquete**. Para obtener más información, consulte [Cómo: personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Elija la **avanzadas** ficha.  
  
3.  En el **ensamblados adicionales** panel, elija el ensamblado personalizado que desea eliminar.  
  
4.  Elija la **eliminar** botón.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Para eliminar un control seguro de un ensamblado  
  
1.  Abra la **Editar ensamblado existente** cuadro de diálogo. Para ello, abra el Diseñador de paquetes, elija la **avanzadas** ficha, elija un ensamblado y, a continuación, elija la **editar** botón.  
  
2.  Elija el control seguro que desee eliminar.  
  
3.  Elija la tecla Supr.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Para eliminar un recurso de clase de un ensamblado  
  
1.  Abra la **Editar ensamblado existente** cuadro de diálogo. Para ello, abra el Diseñador de paquetes, elija la **avanzadas** ficha, elija un ensamblado y, a continuación, elija la **editar** botón.  
  
2.  Elija el recurso de clase que desee eliminar.  
  
3.  Elija la tecla Supr.  
  
## <a name="see-also"></a>Vea también  
 [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
  