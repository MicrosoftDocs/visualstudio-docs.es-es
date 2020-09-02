---
title: '&lt;&gt;elemento customErrorReporting (implementación ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: b7e8a0db3e10a277fe1c4a2f8fcd2bb85fa69e69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187830"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;&gt;elemento customErrorReporting (implementación ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica un URI que se va a mostrar cuando se produce un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Comentarios  
 Este elemento es opcional. Sin ella, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] muestra un cuadro de diálogo de error que muestra la pila de excepciones. Si el `customErrorReporting` elemento está presente, mostrará [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] en su lugar el URI indicado por el `uri` parámetro. El URI de destino incluirá la clase de excepción externa, la clase de excepción interna y el mensaje de excepción interna como parámetros.  
  
 Use este elemento para agregar funcionalidad de informes de errores a la aplicación. Puesto que el URI generado incluye información sobre el tipo de error, el sitio web puede analizar la información y mostrar, por ejemplo, una pantalla de solución de problemas adecuada.  
  
## <a name="example"></a>Ejemplo  
 En el fragmento de código siguiente se muestra el `customErrorReporting` elemento, junto con el URI generado que puede producir.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Consulte también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)
