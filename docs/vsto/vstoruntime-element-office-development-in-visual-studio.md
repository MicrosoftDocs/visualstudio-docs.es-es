---
title: "Elemento &lt;vstoRuntime&gt; (desarrollo de Office en Visual Studio)"
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
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <vstoRuntime>"
  - "<vstoRuntime> (elemento)"
  - "vstoRuntime (elemento)"
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Elemento &lt;vstoRuntime&gt; (desarrollo de Office en Visual Studio)
  El elemento `vstoRuntime` del espacio de nombres `vstav3`  contiene una versión compatible de Visual Studio Tools para Office Runtime para una solución de Office concreta.  
  
## Sintaxis  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## Elementos y atributos  
 El elemento `vstoRuntime` es obligatorio y se encuentra en el espacio de nombres `vstav3` . Si una solución de Office admite dos versiones de Visual Studio Tools para Office Runtime, hay dos elementos `vstoRuntime` en el manifiesto de aplicación.  
  
 El elemento `vstoRuntime` tiene los atributos siguientes:  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`release`|Obligatorio. Versión de lanzamiento de Visual Studio Tools para Office Runtime.|  
|`version`|Obligatorio. Número de versión de Visual Studio Tools para Office Runtime.|  
|`supportUrl`|Opcional. Vínculo a la ubicación de instalación de Visual Studio Tools para Office Runtime.|  
  
 `vstoRuntime` no tiene elementos.  
  
## Ejemplo  
 En el siguiente ejemplo de código, se muestra el elemento `vstoRuntime` en un manifiesto de aplicación para una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime release="VSTOR40Beta1" version="10.0.20303" supportUrl="http://www.microsoft.com" />  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  