---
title: "Elemento &lt;customHostSpecified&gt; (desarrollo de Office en Visual Studio)"
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
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <customHostSpecified>"
  - "elemento <customHostSpecified>"
  - "customHostSpecified (elemento)"
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Elemento &lt;customHostSpecified&gt; (desarrollo de Office en Visual Studio)
  El elemento `customHostSpecified` indica que esta solución no es una aplicación independiente.  Las soluciones de Office incluyen componentes hospedados dentro de las aplicaciones de Microsoft Office.  
  
## Sintaxis  
  
```  
<customHostSpecified />  
```  
  
## Elementos y atributos  
 El elemento `customHostSpecified` es obligatorio para soluciones de Office.  Este elemento está en el espacio de nombres `co.v1` y especifica que esta implementación contiene un componente que se implementará dentro de un host personalizado y no es una aplicación independiente.  
  
 Este elemento es un elemento secundario del primer elemento `<entrypoint>` del manifiesto de aplicación.  No puede haber ningún otro elemento secundario en ese elemento `<entrypoint>`; de lo contrario, [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] provoca un error de validación durante la instalación.  
  
 Este elemento no tiene ningún atributo ni elementos secundarios.  
  
## Ejemplo  
 El ejemplo de código siguiente se muestra el elemento de `customHostSpecified` en un manifiesto de aplicación para una solución de Office.  Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  