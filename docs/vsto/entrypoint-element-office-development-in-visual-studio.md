---
title: '&lt;punto de entrada&gt; elemento (desarrollo de Office en Visual Studio) | Documentos de Microsoft'
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
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9366e3439ed636a2c856ef26c858a7383002a0e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;punto de entrada&gt; elemento (desarrollo de Office en Visual Studio)
  Cada elemento `entryPoint` del espacio de nombres `vstav3` identifica un ensamblado de personalización que se debe ejecutar cuando esta aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] se instala.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|`class`|Obligatorio. Identifica un ensamblado de personalización que se va a ejecutar. La sintaxis de este atributo es *NamespaceName.ClassName*.|  
  
 `entryPoint` tiene el siguiente elemento.  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Obligatorio. El elemento `assemblyIdentity` en el espacio de nombres `vstav3` hace referencia a un elemento `assemblyIdentity` en el manifiesto de aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .  
  
 El rol de `assemblyIdentity` y sus atributos se definen en [&#60; assemblyIdentity &#62; Elemento &#40; Aplicación ClickOnce &#41; ](/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento  
  
### <a name="description"></a>Descripción  
 El ejemplo de código siguiente muestra elementos `entryPoint` en un manifiesto de aplicación para una solución de Office de nivel de documento implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
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
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
### <a name="description"></a>Descripción  
 El ejemplo de código siguiente muestra un elemento `entryPoint` en un manifiesto de aplicación para una solución de Office de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Código  
  
```  
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
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  