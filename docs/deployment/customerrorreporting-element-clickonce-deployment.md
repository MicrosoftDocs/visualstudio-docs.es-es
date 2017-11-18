---
title: "&lt;customErrorReporting&gt; elemento (implementación de ClickOnce) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 238e4c0c0fe9021424b48963eac7d21bf6f9a049
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; elemento (implementación de ClickOnce)
Especifica un URI que se va a mostrar cuando se produce un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Comentarios  
 Este elemento es opcional. Sin él, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] muestra un cuadro de diálogo de error que muestra la pila de excepciones. Si el `customErrorReporting` elemento está presente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en su lugar se mostrará el URI indicado por el `uri` parámetro. El URI de destino incluirá la clase de excepción externa, la clase de excepción interna y el mensaje de excepción interna como parámetros.  
  
 Utilice este elemento para agregar funcionalidad a la aplicación de los informes de errores. Dado que el URI generado incluye información sobre el tipo de error, el sitio Web puede analizar esa información y mostrar, por ejemplo, una pantalla de solución de problemas adecuada.  
  
## <a name="example"></a>Ejemplo  
 El siguiente fragmento de código se muestra la `customErrorReporting` elemento, junto con el URI generado que se podría producir.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)