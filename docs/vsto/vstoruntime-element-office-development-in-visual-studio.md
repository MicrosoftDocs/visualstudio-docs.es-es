---
title: '&lt;vstoRuntime&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 048ad687b8754d09bd1e217e49bee2898d7791e3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime&gt; elemento (desarrollo de Office en Visual Studio)
  El elemento `vstoRuntime` del espacio de nombres `vstav3` contiene una versión compatible de Visual Studio Tools para Office Runtime para una solución de Office concreta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|`release`|Requerido. Versión de lanzamiento de Visual Studio Tools para Office Runtime.|  
|`version`|Requerido. Número de versión de Visual Studio Tools para Office Runtime.|  
|`supportUrl`|Opcional. Vínculo a la ubicación de instalación de Visual Studio Tools para Office Runtime.|  
  
 `vstoRuntime` no tiene elementos.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo de código, se muestra el elemento `vstoRuntime` en un manifiesto de aplicación para una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  