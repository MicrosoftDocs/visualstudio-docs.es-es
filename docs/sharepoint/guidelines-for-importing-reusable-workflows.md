---
title: Directrices para importar flujos de trabajo reutilizables | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bb386a2d80931ece415b0b3939f2947678808261
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62557193"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Directrices para importar flujos de trabajo reutilizables
  Para importar flujos de trabajo reutilizables creados en SharePoint Designer, use la plantilla de proyecto importar flujo de trabajo de SharePoint 2010 reutilizable de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Esta plantilla importa un *flujo de trabajo* *declarativo* ( [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] solo) y lo convierte en un *flujo de trabajo de código*, que es un flujo de trabajo que se puede mejorar con o mediante [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] código. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Tutorial: importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

 Sin embargo, la plantilla de flujo de trabajo importar reutilizable de SharePoint 2010 solo puede importar soluciones de granja. Si desea implementar el flujo de trabajo como una solución en espacio aislado, impórtelo con la plantilla importar paquete de solución de SharePoint 2010. Sin embargo, al hacerlo, no se puede convertir al flujo de trabajo de código y no podrá modificarlo como tal.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importar flujos de trabajo reutilizables mediante la plantilla importar flujo de trabajo reutilizable
 Si importa un flujo de trabajo reutilizable mediante la plantilla de flujo de trabajo importar reutilizable de SharePoint 2010, puede ejecutar o cambiar la solución como cualquier otra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solución de SharePoint, pero es posible que tenga que corregir manualmente algunos elementos.

### <a name="import-task-forms"></a>Importar formularios de tareas
 La plantilla de proyecto importar flujo de trabajo de SharePoint 2010 reutilizable importa todos los formularios de inicio y asociación, pero importa solo un formulario de tareas porque el esquema de flujo de trabajo de código solo permite un formulario de tarea. Los formularios de tareas adicionales de la solución de flujo de trabajo original se colocan en la carpeta **otros archivos importados** en **Explorador de soluciones**.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importar flujos de trabajo reutilizables mediante la plantilla importar paquete de solución de SharePoint 2010
 Si importa un flujo de trabajo reutilizable mediante la plantilla importar paquete de solución de SharePoint 2010, debe tener en cuenta los siguientes problemas:

- Después de importar el flujo de trabajo, puede implementarlo y ejecutarlo inmediatamente en eligiendo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] la tecla **F5** . Sin embargo, si cambia algo en el flujo de trabajo en la solución importada, es posible que tenga que corregir manualmente los elementos del proyecto para poder implementar y ejecutar el flujo de trabajo.

- Dado que el flujo de trabajo es declarativo, no se le puede agregar código. Para convertir el flujo de trabajo en un flujo de trabajo de código, debe importarlo en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mediante la plantilla de flujo de trabajo importar reutilizable de SharePoint 2010.

- Aunque puede editar el archivo del diseñador de flujo de trabajo (. xoml) en Vista de diseño, se recomienda editarlo en la vista Código fuente, ya que el diseñador de flujo de trabajo muestra los errores falsos.

- La depuración en el flujo de trabajo no funciona para el contenido declarativo. No se alcanzan los puntos de interrupción establecidos en [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] .

## <a name="import-globally-reusable-workflow-solutions"></a>Importar soluciones de flujo de trabajo reutilizables globalmente
 Los flujos de trabajo reutilizables globalmente no se pueden importar mediante la plantilla de flujo de trabajo importar reutilizable de SharePoint 2010. Para importar un flujo de trabajo reutilizable globalmente, tiene que convertirlo en un flujo de trabajo que no se puede reutilizar globalmente o tener que usar la plantilla importar paquete de solución de SharePoint 2010.

 Para convertir el flujo de trabajo, haga una copia del flujo de trabajo reutilizable globalmente en SharePoint Designer (abriendo el menú contextual del flujo de trabajo y, a continuación, eligiendo **Guardar como copia**). A continuación, importe el nuevo flujo de trabajo reutilizable con la plantilla de flujo de trabajo importar reutilizable de SharePoint 2010 en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Para importar el flujo de trabajo reutilizable globalmente sin modificarlo, use la plantilla importar paquete de solución de SharePoint 2010. Si usa este método, el flujo de trabajo no se convierte en un flujo de trabajo de código y sigue siendo un flujo de trabajo declarativo.

## <a name="see-also"></a>Consulte también
- [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Tutorial: importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
