---
title: "Elemento &lt;entryPoint&gt; (desarrollo de Office en Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <entryPoint>"
  - "elemento <entryPoint>"
  - "entryPoint (elemento)"
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Elemento &lt;entryPoint&gt; (desarrollo de Office en Visual Studio)
  Cada elemento `entryPoint` del espacio de nombres `vstav3`  identifica un ensamblado de personalización que se debe ejecutar cuando esta aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] se instala.  
  
## Sintaxis  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## Elementos y atributos  
 El elemento `entryPoint` es necesario y se encuentra en el espacio de nombres `vstav3` .  
  
 Cada elemento `entryPoint` puede contener solo un ensamblado de personalización. Puede haber numerosos elementos `entryPoint` en un manifiesto de aplicación.  
  
 El elemento `entryPoint` tiene los atributos siguientes:  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`class`|Obligatorio. Identifica un ensamblado de personalización que se va a ejecutar. La sintaxis de este atributo es *NamespaceName.ClassName*.|  
  
 `entryPoint` tiene el siguiente elemento.  
  
### assemblyIdentity  
 Requerido. El elemento `assemblyIdentity` en el espacio de nombres `vstav3`  hace referencia a un elemento `assemblyIdentity` en el manifiesto de aplicación [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)].  
  
 El rol de `assemblyIdentity` y sus atributos se definen en [Elemento &#60;assemblyIdentity&#62; &#40;Aplicación ClickOnce&#41;](~/deployment/assemblyidentity-element-clickonce-application.md).  
  
## Ejemplo de personalización de nivel de documento  
  
### Descripción  
 El ejemplo de código siguiente muestra elementos `entryPoint` en un manifiesto de aplicación para una solución de Office de nivel de documento implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## Ejemplo para complemento de VSTO  
  
### Descripción  
 El ejemplo de código siguiente muestra un elemento `entryPoint` en un manifiesto de aplicación para una solución de Office de nivel de aplicación implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  