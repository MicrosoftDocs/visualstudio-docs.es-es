---
title: '&lt;postAction&gt; elemento (desarrollo de Office en Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34ebc9595b8b66ac4d81f5a7adef86a14b4d2a58
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802166"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `postAction` del espacio de nombres `vstav3` , contiene todos los elementos `entrypoint` y todos los elementos `postActionData` asociados a acciones posteriores a la implementación, que se ejecutan una vez instaladas las soluciones de Office.

## <a name="syntax"></a>Sintaxis

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Los elementos y atributos
 El elemento `postAction` es opcional y se encuentra en el espacio de nombres `vstav3` . Hay un elemento `postAction` definido en el manifiesto de aplicación de cada acción posterior a la implementación.

 El elemento `postAction` no tiene atributos.

 `postAction` tiene los siguientes elementos:

### <a name="entrypoint"></a>entrypoint
 Opcional. El rol de la `entryPoint` elemento en el `vstav3` espacio de nombres se define en [ &#60;entryPoints&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 Opcional. El rol de la `postActionData` elemento en el `vstav3` espacio de nombres se define en [ &#60;postActionData&#62; elemento &#40;desarrollo de Office en Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Ejemplo de acción posterior a la implementación

### <a name="description"></a>Descripción
 En el siguiente ejemplo de código, se muestra el elemento `postAction` en un manifiesto de aplicación para una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
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

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
