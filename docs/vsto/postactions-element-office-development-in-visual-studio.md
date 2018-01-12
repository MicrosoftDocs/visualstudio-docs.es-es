---
title: '&lt;postActions&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bbe0708ce97eb6410f006b6dcdc8d8194907b9c1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postActions&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `postActions` del espacio de nombres `vstav3` , contiene todos los elementos `postAction` que describen las acciones posteriores a la implementación y que se ejecutan una vez instaladas las soluciones de Office.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `postActions` es opcional y se encuentra en el espacio de nombres `vstav3` . Solo hay un elemento `postActions` definido en un manifiesto de la aplicación.  
  
 El elemento `postActions` no tiene atributos.  
  
 `postActions` tiene el siguiente elemento.  
  
### <a name="postaction"></a>postAction  
 Opcional. El rol de la `postAction` elemento en el `vstav3` espacio de nombres se define en [&#60; postAction &#62; Elemento &#40; desarrollo de Office en Visual Studio &#41; ](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Ejemplo de acciones posteriores a la implementación.  
  
### <a name="description"></a>Descripción  
 En el siguiente ejemplo de código, se muestra el elemento `postActions` en el manifiesto de aplicación de una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:postActions>  
  <vstav3:postAction>  
    <vstav3:entryPoint   
      class="PostDeploymentAction.PostDeploymentActionSample">  
      <assemblyIdentity   
        name="PostDeploymentAction"   
        version="1.0.0.0"   
        language="neutral"   
        processorArchitecture="msil" />  
    </vstav3:entryPoint>  
    <vstav3:postActionData>  
    </vstav3:postActionData>  
  </vstav3:postAction>  
</vstav3:postActions>  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  