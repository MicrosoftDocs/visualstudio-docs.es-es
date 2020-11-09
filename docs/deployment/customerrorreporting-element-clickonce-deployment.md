---
title: '&lt;&gt;elemento customErrorReporting (implementación ClickOnce) | Microsoft Docs'
description: El elemento customErrorReporting especifica un URI que se muestra cuando se produce un error en lugar de un cuadro de diálogo de error que muestra la pila de excepciones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5576912fb428e15a6f8164e52d558e255e184fe3
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382525"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;&gt;elemento customErrorReporting (implementación ClickOnce)
Especifica un URI que se va a mostrar cuando se produce un error.

## <a name="syntax"></a>Sintaxis

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Comentarios
 Este elemento es opcional. Sin ella, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] muestra un cuadro de diálogo de error que muestra la pila de excepciones. Si el `customErrorReporting` elemento está presente, mostrará [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en su lugar el URI indicado por el `uri` parámetro. El URI de destino incluirá la clase de excepción externa, la clase de excepción interna y el mensaje de excepción interna como parámetros.

 Use este elemento para agregar funcionalidad de informes de errores a la aplicación. Puesto que el URI generado incluye información sobre el tipo de error, el sitio web puede analizar la información y mostrar, por ejemplo, una pantalla de solución de problemas adecuada.

## <a name="example"></a>Ejemplo
 En el fragmento de código siguiente se muestra el `customErrorReporting` elemento, junto con el URI generado que puede producir.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>Vea también
- [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)