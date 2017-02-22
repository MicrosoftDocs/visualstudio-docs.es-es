---
title: "Elemento &lt;customErrorReporting&gt; (Implementaci&#243;n ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<customErrorReporting> (elemento) [manifiesto de implementación ClickOnce]"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;customErrorReporting&gt; (Implementaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica un URI que se va a mostrar cuando se produce un error.  
  
## Sintaxis  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## Comentarios  
 Este elemento es opcional.  Sin él, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] abre un cuadro de diálogo de error en el que se muestra la pila de la excepción.  Si el elemento `customErrorReporting` está presente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mostrará en su lugar el URI indicado por el parámetro `uri`.  El URI de destino incluirá la clase de excepción externa, la clase de excepción interna y el mensaje de excepción interno como parámetros.  
  
 Utilice este elemento para agregar la funcionalidad de generación de informes de errores a su aplicación.  Dado que el URI generado contiene información sobre el tipo de error, el sitio web puede analizar esa información y mostrar, por ejemplo, una pantalla de solución de problemas adecuada.  
  
## Ejemplo  
 En el fragmento de código siguiente se muestra el elemento `customErrorReporting`, junto con el URI generado que podría producir.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)