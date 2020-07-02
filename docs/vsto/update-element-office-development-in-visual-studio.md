---
title: '&lt;&gt;elemento Update (desarrollo de Office en Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241bddb8c79a01bb1ba6921486a4dc46d99940cc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537389"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento Update (desarrollo de Office en Visual Studio)
  El `update` elemento especifica el intervalo en el que la solución comprobará si hay actualizaciones.

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

## <a name="elements-and-attributes"></a>Elementos y atributos
 El elemento `update` es obligatorio y se encuentra en el espacio de nombres `vstav3` .

 El elemento `update` tiene los atributos siguientes:

|Atributo|Descripción|
|---------------|-----------------|
|`enabled`|Obligatorio. Establezca habilitado en uno de los siguientes valores:<br /><br /> -   **true** para comprobar si hay actualizaciones.<br />-   **false** para evitar la comprobación de actualizaciones.|

 El elemento `update` tiene los siguientes elementos secundarios.

### <a name="expiration"></a>expiration
 El elemento `expiration` es obligatorio y se encuentra en el espacio de nombres `vstav3` . Este elemento especifica el intervalo en el que la solución busca actualizaciones.

 El elemento `expiration` tiene los atributos siguientes:

|Atributo|Descripción|
|---------------|-----------------|
|`maximumAge`| Obligatorio. Establezca este valor en un entero.|
|`unit`|Obligatorio. Establezca `unit` en uno de los valores siguientes:<br /><br /> -   **después**<br />-   **durante**<br />-   **próximas**|

## <a name="example-of-always-checking-for-updates"></a>Ejemplo de comprobación de actualizaciones siempre

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se muestra un `update` elemento que se establece para comprobar siempre si hay actualizaciones en las soluciones de Office.

### <a name="code"></a>Código

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Ejemplo de configuración de un intervalo de actualización predeterminado

### <a name="description"></a>Descripción
 En el ejemplo de código siguiente se muestra un `update` elemento en un manifiesto de aplicación para las soluciones de Office. Este ejemplo de código forma parte de un ejemplo más grande proporcionado en los [manifiestos de aplicación para las soluciones de Office](../vsto/application-manifests-for-office-solutions.md).

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
