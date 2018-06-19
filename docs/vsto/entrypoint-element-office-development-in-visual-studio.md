---
title: '&lt;punto de entrada&gt; elemento (desarrollo de Office en Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6eb617b44eb5360ea8c313431c7d8609505efa16
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447094"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;punto de entrada&gt; elemento (desarrollo de Office en Visual Studio)
  Cada elemento `entryPoint` del espacio de nombres `vstav3` identifica un ensamblado de personalización que se debe ejecutar cuando esta aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] se instala.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El elemento `entryPoint` es necesario y se encuentra en el espacio de nombres `vstav3` .  
  
 Cada elemento `entryPoint` puede contener solo un ensamblado de personalización. Puede haber numerosos elementos `entryPoint` en un manifiesto de aplicación.  
  
 El elemento `entryPoint` tiene los atributos siguientes:  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`class`|Requerido. Identifica un ensamblado de personalización que se va a ejecutar. La sintaxis de este atributo es *NamespaceName.ClassName*.|  
  
 `entryPoint` tiene el siguiente elemento.  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Requerido. El elemento `assemblyIdentity` en el espacio de nombres `vstav3` hace referencia a un elemento `assemblyIdentity` en el manifiesto de aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
 El rol de `assemblyIdentity` y sus atributos se definen en [ &#60;assemblyIdentity&#62; elemento &#40;aplicación ClickOnce&#41;](/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento  
  
### <a name="description"></a>Descripción  
 El ejemplo de código siguiente muestra elementos `entryPoint` en un manifiesto de aplicación para una solución de Office de nivel de documento implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.ThisWorkbook">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet1">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet2">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
<vstav3:entryPoint   
  class="ContosoExcelWorkbook.Sheet3">  
  <assemblyIdentity   
    name="ContosoExcelWorkbook"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="vsto-add-in-example"></a>Ejemplo para complemento de VSTO  
  
### <a name="description"></a>Descripción  
 El ejemplo de código siguiente muestra un elemento `entryPoint` en un manifiesto de aplicación para una solución de Office de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```xml
<vstav3:entryPoint   
  class="ContosoOutlookAddIn.ThisAddIn">  
  <assemblyIdentity   
    name="ContosoOutlookAddIn"   
    version="1.0.0.0"   
    language="neutral"   
    processorArchitecture="msil" />  
</vstav3:entryPoint>  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  