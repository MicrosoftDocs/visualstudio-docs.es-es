---
title: '&lt;postActionData&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ea65f8789e3106abe8da46ae0302cdf0f4f47ef7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `postActionData` del espacio de nombres `vstav3` especifica los datos asociados a cualquier acción posterior a la implementación que se ejecuta tras la instalación de soluciones de Office.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<postActionData>  
</postActionData>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `postActionData` es opcional y se encuentra en el espacio de nombres `vstav3` . Hay un elemento `postActionData` definido en el manifiesto de aplicación de cada acción posterior a la implementación.  
  
 El elemento `postActions` no tiene atributos.  
  
 `postActions` no tiene elementos secundarios.  
  
## <a name="post-deployment-action-example"></a>Ejemplo de acciones posteriores a la implementación.  
  
### <a name="description"></a>Descripción  
 En el siguiente ejemplo de código, se muestra el elemento `postAction` en un manifiesto de aplicación para una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:postActionData>  
  data in any format  
</vstav3:postActionData>  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  