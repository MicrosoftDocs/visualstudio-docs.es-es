---
title: 'Cómo: agregar un archivo de recursos | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0091054c0c0d2cfb7f19f2ca46839cfdcf47832b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861194"
---
# <a name="how-to-add-a-resource-file"></a>Cómo: agregar un archivo de recursos
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
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
