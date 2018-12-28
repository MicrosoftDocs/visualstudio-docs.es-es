---
title: '&lt;actualizar&gt; elemento (desarrollo de Office en Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec520c140dedf3a5bb93ebd5f17f8751687abcac
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53805015"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;actualizar&gt; elemento (desarrollo de Office en Visual Studio)
  El `update` elemento especifica el intervalo en el que se comprobará la solución de actualizaciones.

## <a name="syntax"></a>Sintaxis

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>Los elementos y atributos
 El elemento `update` es obligatorio y se encuentra en el espacio de nombres `vstav3` .

 El elemento `update` tiene los atributos siguientes:

|Atributo|Descripción|
|---------------|-----------------|
|`enabled`|Obligatorio. Establezca enabled en uno de los siguientes valores:<br /><br /> -   **True** para comprobar si hay actualizaciones.<br />-   **false** para evitar la comprobación de actualizaciones.|

 El elemento `update` tiene los siguientes elementos secundarios.

### <a name="expiration"></a>expiración
 El elemento `expiration` es obligatorio y se encuentra en el espacio de nombres `vstav3` . Este elemento especifica el intervalo en el que se comprueba la solución de actualizaciones.

 El elemento `expiration` tiene los atributos siguientes:

|Atributo|Descripción|
|---------------|-----------------|
|`maximumAge`| Obligatorio. Establézcalo en un entero.|
|`unit`|Obligatorio. Establecer `unit` a uno de los siguientes valores:<br /><br /> -   **Horas**<br />-   **Días**<br />-   **semanas**|

## <a name="example-of-always-checking-for-updates"></a>Ejemplo de comprobar siempre las actualizaciones

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se ilustra un `update` elemento que se establece en comprobar siempre las actualizaciones en soluciones de Office.

### <a name="code"></a>Código

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Ejemplo de cómo configurar un intervalo de actualización predeterminado

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se ilustra un `update` elemento en un manifiesto de aplicación para soluciones de Office. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Vea también

- [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
