---
title: '&lt;postActions&gt; elemento (desarrollo de Office en Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6542344d5e0967504eccbedd4986cd80ef04f40a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692579"
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postActions&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `postActions` del espacio de nombres `vstav3` , contiene todos los elementos `postAction` que describen las acciones posteriores a la implementación y que se ejecutan una vez instaladas las soluciones de Office.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
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
 Opcional. El rol de la `postAction` elemento en el `vstav3` espacio de nombres se define en [ &#60;postAction&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Ejemplo de acciones posteriores a la implementación  
  
### <a name="description"></a>Descripción  
 En el siguiente ejemplo de código, se muestra el elemento `postActions` en el manifiesto de aplicación de una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml  
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
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  