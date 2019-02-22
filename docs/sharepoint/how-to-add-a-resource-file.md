---
title: Filtrar Agregar un archivo de recursos | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2fd519b396f5120b7b0acca8d2e6144e363ab1f0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633062"
---
# <a name="how-to-add-a-resource-file"></a>Filtrar Agregar un archivo de recursos
  Los comandos para agregar archivos de recursos está en el menú contextual del nodo de la solución y los nodos de la característica en el Explorador de soluciones. Para obtener más información, consulte [soluciones de SharePoint localizar](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Para agregar un archivo de recursos global a una solución de SharePoint

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra una solución de SharePoint.

2. En **el Explorador de soluciones**, elija un nodo de proyecto de SharePoint y, a continuación, en la barra de menús, elija **proyecto** > **Agregar nuevo elemento**.

3. En el **Agregar nuevo elemento** diálogo cuadro, elija el **archivo de recursos globales** plantilla y, a continuación, elija el **agregar** botón.

   > [!NOTE]
   >  La plantilla de elemento de proyecto de archivo de recursos globales solo aparece cuando se selecciona un elemento de proyecto de SharePoint.

4. En el **Agregar recurso** diálogo cuadro, elija una referencia cultural para el archivo de recursos, como el inglés (Estados Unidos).

    Este paso agrega un archivo de recursos global a la solución en el formato, Resource_x_**.** <em>referencia cultural</em><strong>.</strong> resx, como por ejemplo, *recurso1.en-US.resx*.

5. Cuando el **Editor de recursos** se abre en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], agregar recursos al archivo de recursos.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Para agregar un archivo de recursos de características a una característica de SharePoint

1.  Si no está abierta en la solución de SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra la solución.

2.  En **el Explorador de soluciones**, abra el menú contextual para el nombre de una característica en el **características** nodo y, a continuación, elija **Agregar recurso de características**.

     Este paso agrega un archivo de recursos a la característica en el formato, _NombreArchivoRecursos_**.** _referencia cultural_**.resx**, como por ejemplo, *Característica1.en-US.resx*.

3.  Cuando el **Editor de recursos** se abre en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], agregar recursos al archivo de recursos.

## <a name="see-also"></a>Vea también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
