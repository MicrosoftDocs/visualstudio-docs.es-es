---
title: 'Cómo: agregar un archivo de recursos | Microsoft Docs'
description: Agregue un archivo de recursos en Visual Studio mediante los comandos del menú contextual del nodo de solución y los nodos de características en Explorador de soluciones.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 22b5638f7251b34c74da348e55e755cd27132aff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934850"
---
# <a name="how-to-add-a-resource-file"></a>Cómo: para agregar un archivo de recursos
  Los comandos para agregar archivos de recursos se encuentra en el menú contextual del nodo de solución y los nodos de características de Explorador de soluciones. Para obtener más información, vea [localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Para agregar un archivo de recursos global a una solución de SharePoint

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , abra una solución de SharePoint.

2. En **Explorador de soluciones**, elija un nodo de proyecto de SharePoint y, a continuación, en la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , elija la plantilla **archivo de recursos globales** y, a continuación, elija el botón **Agregar** .

   > [!NOTE]
   > La plantilla de elemento de proyecto archivo de recursos globales solo aparece cuando se selecciona un elemento de proyecto de SharePoint.

4. En el cuadro de diálogo **Agregar recurso** , elija una referencia cultural para el archivo de recursos, como inglés (Estados Unidos).

    En este paso se agrega un archivo de recursos global a la solución con el formato Resource_x_ **.** <em>referencia cultural</em><strong>.</strong> resx, como, *Resource1. en-US. resx*.

5. Cuando se abra el **Editor de recursos** en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , agregue recursos al archivo de recursos.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Para agregar un archivo de recursos de características a una característica de SharePoint

1. Si la solución de SharePoint todavía no está abierta en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , abra la solución.

2. En **Explorador de soluciones**, abra el menú contextual del nombre de una característica en el nodo **características** y, a continuación, elija **Agregar recurso de característica**.

     En este paso se agrega un archivo de recursos a la característica con el formato _nombrearchivorecursos_**.** _Culture_.**resx**, como, *Feature1. en-US. resx*.

3. Cuando se abra el **Editor de recursos** en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , agregue recursos al archivo de recursos.

## <a name="see-also"></a>Consulte también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
