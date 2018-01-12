---
title: "Cómo: agregar un archivo de recursos | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 47cae5fac3ddbcbc34535176701d0293ae4f66ba
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-resource-file"></a>Cómo: Agregar un archivo de recursos
  Los comandos para agregar archivos de recursos está en el menú contextual de los nodos de la característica en el Explorador de soluciones y el nodo de la solución. Para obtener más información, consulte [localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Para agregar un archivo de recursos global a una solución de SharePoint  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra una solución de SharePoint.  
  
2.  En **el Explorador de soluciones**, elija un nodo de proyecto de SharePoint y, a continuación, en la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** diálogo cuadro, elija la **archivo de recursos globales** plantilla y, a continuación, elija la **agregar** botón.  
  
    > [!NOTE]  
    >  La plantilla de elemento de proyecto de archivo de recursos globales solo aparece cuando se selecciona un elemento de proyecto de SharePoint.  
  
4.  En el **Agregar recurso** diálogo cuadro, elija una referencia cultural para el archivo de recursos, como el inglés (Estados Unidos).  
  
     Este paso agrega un archivo de recursos global a la solución en el formato, recursos*x***.** *referencia cultural***.** resx, por ejemplo, recurso1.en-US.resx.  
  
5.  Cuando el **Editor de recursos** se abre en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], agregar recursos al archivo de recursos.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Para agregar un archivo de recursos de características a una característica de SharePoint  
  
1.  Si no está abierta en la solución de SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra la solución.  
  
2.  En **el Explorador de soluciones**, abra el menú contextual para el nombre de una característica en el **características** nodo y, a continuación, elija **Agregar recurso de características**.  
  
     Este paso agrega un archivo de recursos a la característica en el formato, *NombreArchivoRecursos***.** *referencia cultural***.** resx, por ejemplo, Característica1.en-US.resx.  
  
3.  Cuando el **Editor de recursos** se abre en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], agregar recursos al archivo de recursos.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  