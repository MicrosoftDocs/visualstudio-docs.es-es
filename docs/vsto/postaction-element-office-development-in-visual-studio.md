---
title: '&lt;postAction&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 581ef7bafc075419df8e2dfb1731b334a9564455
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `postAction` del espacio de nombres `vstav3` , contiene todos los elementos `entrypoint` y todos los elementos `postActionData` asociados a acciones posteriores a la implementación, que se ejecutan una vez instaladas las soluciones de Office.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `postAction` es opcional y se encuentra en el espacio de nombres `vstav3` . Hay un elemento `postAction` definido en el manifiesto de aplicación de cada acción posterior a la implementación.  
  
 El elemento `postAction` no tiene atributos.  
  
 `postAction` tiene los siguientes elementos:  
  
### <a name="entrypoint"></a>entrypoint  
 Opcional. El rol de la `entryPoint` elemento en el `vstav3` espacio de nombres se define en [&#60; entryPoints &#62; Elemento &#40; desarrollo de Office en Visual Studio &#41; ](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### <a name="postactiondata"></a>postActionData  
 Opcional. El rol de la `postActionData` elemento en el `vstav3` espacio de nombres se define en [&#60; postActionData &#62; Elemento &#40; desarrollo de Office en Visual Studio &#41; ](../vsto/postactiondata-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Ejemplo de acciones posteriores a la implementación.  
  
### <a name="description"></a>Descripción  
 En el siguiente ejemplo de código, se muestra el elemento `postAction` en un manifiesto de aplicación para una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
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
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  