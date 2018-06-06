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
ms.openlocfilehash: c51a7f79165d421f080d05088418d02a48680b66
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767613"
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
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `update` es obligatorio y se encuentra en el espacio de nombres `vstav3`.  
  
 El `update` elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`enabled`|Requerido. Establezca enabled en uno de los siguientes valores:<br /><br /> -   **True** para buscar actualizaciones.<br />-   **false** para evitar la comprobación de actualizaciones.|  
  
 El `update` elemento tiene los siguientes elementos secundarios.  
  
### <a name="expiration"></a>expiración  
 El elemento `expiration` es obligatorio y se encuentra en el espacio de nombres `vstav3`. Este elemento especifica el intervalo en el que se comprueba la solución de actualizaciones.  
  
 El `expiration` elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`maximumAge`|   Requerido. Establezca esto en un entero.|  
|`unit`|Requerido. Establecer `unit` a uno de los siguientes valores:<br /><br /> -   **Horas**<br />-   **Días**<br />-   **Semanas**|  
  
## <a name="example-of-always-checking-for-updates"></a>Ejemplo de comprobar siempre las actualizaciones  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra un `update` elemento que se establece para que siempre busque actualizaciones en soluciones de Office.  
  
### <a name="code"></a>Código  
  
```xml  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Ejemplo de configuración de un intervalo de actualización predeterminado  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra un `update` elemento en un manifiesto de aplicación para soluciones de Office. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Vea también  
 [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  