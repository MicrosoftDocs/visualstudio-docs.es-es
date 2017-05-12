---
title: "Elemento &lt;postActionData&gt; (desarrollo de Office en Visual Studio)"
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
  - "Elemento <postActionData>"
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio], elemento <postActionData>"
  - "postActionData (elemento)"
ms.assetid: e36cbd64-fd27-4413-b293-cf5546fbdfaf
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Elemento &lt;postActionData&gt; (desarrollo de Office en Visual Studio)
  El elemento `postActionData` del espacio de nombres `vstav3`  especifica los datos asociados a cualquier acción posterior a la implementación que se ejecuta tras la instalación de soluciones de Office.  
  
## Sintaxis  
  
```  
<postActionData>  
</postActionData>  
```  
  
## Elementos y atributos  
 El elemento `postActionData` es opcional y se encuentra en el espacio de nombres `vstav3` . Hay un elemento `postActionData` definido en el manifiesto de aplicación de cada acción posterior a la implementación.  
  
 El elemento `postActions` no tiene atributos.  
  
 `postActions` no tiene elementos secundarios.  
  
## Ejemplo de acciones posteriores a la implementación.  
  
### Descripción  
 En el siguiente ejemplo de código, se muestra el elemento `postAction` en un manifiesto de aplicación para una solución de Office implementada mediante [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este ejemplo de código forma parte de un ejemplo más extenso incluido en [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).  
  
### Código  
  
```  
<vstav3:postActionData> data in any format </vstav3:postActionData>  
```  
  
## Vea también  
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)  
  
  