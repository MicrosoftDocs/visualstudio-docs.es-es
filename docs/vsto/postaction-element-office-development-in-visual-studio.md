---
title: '&lt;elemento postaction &gt; (desarrollo de Office en Visual Studio)'
description: El elemento postaction del espacio de nombres vstav3 contiene los elementos EntryPoint y todos los elementos postActionData asociados a acciones posteriores a la implementación, que se ejecutan una vez instaladas las soluciones de Office.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04f8c92c52aeee9f7f1dd5ab67b3dcef3a295474
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470058"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;elemento postaction &gt; (desarrollo de Office en Visual Studio)
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

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `postAction` es opcional y se encuentra en el espacio de nombres `vstav3` . Hay un elemento `postAction` definido en el manifiesto de aplicación de cada acción posterior a la implementación.

 El elemento `postAction` no tiene atributos.

 `postAction` tiene los siguientes elementos.

### <a name="entrypoint"></a>entryPoint
 Opcional. El rol del `entryPoint` elemento en el `vstav3` espacio de nombres se define en [&#60;elemento&#62; entryPoints &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 Opcional. El rol del `postActionData` elemento en el `vstav3` espacio de nombres se define en [&#60;elemento&#62; postActionData &#40;el desarrollo de Office en Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Ejemplo de acción posterior a la implementación

### <a name="description"></a>Descripción
 En el siguiente ejemplo de código, se muestra el elemento `postAction` en un manifiesto de aplicación para una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="see-also"></a>Consulte también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
