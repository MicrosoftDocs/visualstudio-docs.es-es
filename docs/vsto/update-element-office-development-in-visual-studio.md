---
title: '&lt;actualizar&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
ms.openlocfilehash: 2f0e1fdc26e285ce9b6a1fd5ecc1aa638fe909b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;actualizar&gt; elemento (desarrollo de Office en Visual Studio)
  El `update` elemento especifica el intervalo en el que se comprobará la solución de actualizaciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|`maximumAge`|-Required. Establezca esto en un entero.|  
|`unit`|Requerido. Establecer `unit` a uno de los siguientes valores:<br /><br /> -   **Horas**<br />-   **Días**<br />-   **Semanas**|  
  
## <a name="example-of-always-checking-for-updates"></a>Ejemplo de comprobar siempre las actualizaciones  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra un `update` elemento que se establece para que siempre busque actualizaciones en soluciones de Office.  
  
### <a name="code"></a>Código  
  
```  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Ejemplo de configuración de un intervalo de actualización predeterminado  
  
### <a name="description"></a>Descripción  
 En el ejemplo de código siguiente se muestra un `update` elemento en un manifiesto de aplicación para soluciones de Office. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Vea también  
 [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  