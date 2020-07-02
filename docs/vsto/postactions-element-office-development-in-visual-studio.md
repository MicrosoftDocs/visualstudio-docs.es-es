---
title: '&lt;elemento postactions &gt; (desarrollo de Office en Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bfe9ae171f0f6fac1c2b5add5340de1c11f3da0f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544422"
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;elemento postactions &gt; (desarrollo de Office en Visual Studio)
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
 Opcional. El rol del `postAction` elemento en el `vstav3` espacio de nombres se define en [&#60;elemento&#62; postaction &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Ejemplo de acción posterior a la implementación

### <a name="description"></a>Descripción
 En el siguiente ejemplo de código, se muestra el elemento `postActions` en el manifiesto de aplicación de una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

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

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
