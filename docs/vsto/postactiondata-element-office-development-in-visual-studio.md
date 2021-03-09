---
title: '&lt;postActionData &gt; (elemento, desarrollo de Office)'
description: El elemento postActionData del espacio de nombres vstav3 especifica los datos asociados a cualquier acción posterior a la implementación que se ejecute una vez instaladas las soluciones de Office.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a75f61c6d1f80a127f49d96c4e3f4910c66dd8aa
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470071"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;postActionData &gt; (elemento, desarrollo de Office)
  El elemento `postActionData` del espacio de nombres `vstav3` especifica los datos asociados a cualquier acción posterior a la implementación que se ejecuta tras la instalación de soluciones de Office.

## <a name="syntax"></a>Sintaxis

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `postActionData` es opcional y se encuentra en el espacio de nombres `vstav3` . Hay un elemento `postActionData` definido en el manifiesto de aplicación de cada acción posterior a la implementación.

 El elemento `postActions` no tiene atributos.

 `postActions` no tiene elementos secundarios.

## <a name="post-deployment-action-example"></a>Ejemplo de acción posterior a la implementación

### <a name="description"></a>Descripción
 En el siguiente ejemplo de código, se muestra el elemento `postAction` en el manifiesto de aplicación de una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Consulte también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
