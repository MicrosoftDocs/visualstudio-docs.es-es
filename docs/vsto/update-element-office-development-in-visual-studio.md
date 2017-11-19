---
title: '&lt;actualizar&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a41e7580e7c6c169554bb50c4d0c9af29a992b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
|`enabled`|Obligatorio. Establezca enabled en uno de los siguientes valores:<br /><br /> -   **True** para buscar actualizaciones.<br />-   **false** para evitar la comprobación de actualizaciones.|  
  
 El `update` elemento tiene los siguientes elementos secundarios.  
  
### <a name="expiration"></a>expiración  
 El elemento `expiration` es obligatorio y se encuentra en el espacio de nombres `vstav3`. Este elemento especifica el intervalo en el que se comprueba la solución de actualizaciones.  
  
 El `expiration` elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`maximumAge`|-Required. Establezca esto en un entero.|  
|`unit`|Obligatorio. Establecer `unit` a uno de los siguientes valores:<br /><br /> -   **horas**<br />-   **días**<br />-   **semanas**|  
  
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
  
  