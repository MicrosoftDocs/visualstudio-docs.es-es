---
title: '&lt;&gt;elemento vstoRuntime (desarrollo de Office en Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c866db5f691db56e68f6980c9c07d21ee15c0ae5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921753"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento vstoRuntime (desarrollo de Office en Visual Studio)
  El elemento `vstoRuntime` del espacio de nombres `vstav3` contiene una versión compatible de Visual Studio Tools para Office Runtime para una solución de Office concreta.

## <a name="syntax"></a>Sintaxis

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `vstoRuntime` es obligatorio y se encuentra en el espacio de nombres `vstav3` . Si una solución de Office admite dos versiones de Visual Studio Tools para Office Runtime, hay dos elementos `vstoRuntime` en el manifiesto de aplicación.

 El elemento `vstoRuntime` tiene los atributos siguientes:

|Atributo|Descripción|
|---------------|-----------------|
|`release`|Necesario. Versión de lanzamiento de Visual Studio Tools para Office Runtime.|
|`version`|Necesario. Número de versión de Visual Studio Tools para Office Runtime.|
|`supportUrl`|Opcional. Vínculo a la ubicación de instalación de Visual Studio Tools para Office Runtime.|

 `vstoRuntime` no tiene elementos.

## <a name="example"></a>Ejemplo
 En el siguiente ejemplo de código, se muestra el elemento `vstoRuntime` en el manifiesto de aplicación de una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Vea también

- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
