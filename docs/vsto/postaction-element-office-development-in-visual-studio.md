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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 63e15e2a02ac58ee385e38d5ed2d435c0e80dddb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
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
  
  