---
title: '&lt;vstoRuntime&gt; elemento (desarrollo de Office en Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 98f483748cce9c3a053c800f9bdd6e0f3d651da2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982137"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime&gt; elemento (desarrollo de Office en Visual Studio)
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
|`release`|Obligatorio. Versión de lanzamiento de Visual Studio Tools para Office Runtime.|
|`version`|Obligatorio. Número de versión de Visual Studio Tools para Office Runtime.|
|`supportUrl`|Opcional. Vínculo a la ubicación de instalación de Visual Studio Tools para Office Runtime.|

 `vstoRuntime` no tiene elementos.

## <a name="example"></a>Ejemplo
 En el siguiente ejemplo de código, se muestra el elemento `vstoRuntime` en un manifiesto de aplicación para una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

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
