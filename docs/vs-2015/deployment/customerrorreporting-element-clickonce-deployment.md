---
title: '&lt;customErrorReporting&gt; elemento (implementación ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 422ccaf8e82a2b1813bc876c76a6ff5a7c96f43c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576673"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; elemento (implementación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ &lt;customErrorReporting&gt; elemento (implementación ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/customerrorreporting-element-clickonce-deployment).  
  
Especifica un URI que se va a mostrar cuando se produce un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Comentarios  
 Este elemento es opcional. Sin él, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] muestra un cuadro de diálogo que muestra la pila de excepciones. Si el `customErrorReporting` elemento está presente, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] en su lugar mostrará el URI indicado por el `uri` parámetro. El URI de destino incluirá la clase de excepción externa, la clase de excepción interna y el mensaje de excepción interna como parámetros.  
  
 Utilice este elemento para agregar funcionalidad a la aplicación de los informes de errores. Dado que el URI generado incluye información sobre el tipo de error, el sitio Web puede analizar esa información y mostrar, por ejemplo, una pantalla de la solución de problemas adecuada.  
  
## <a name="example"></a>Ejemplo  
 El siguiente fragmento muestra el `customErrorReporting` elemento, junto con el URI generado que se podría producir.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)



