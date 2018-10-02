---
title: 'CA2106: Asegurar aserciones | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67d1228b7684b2ba00a7e64f3755fb107fa0e75b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591877"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Asegurar aserciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA2106: asegurar aserciones](https://docs.microsoft.com/visualstudio/code-quality/ca2106-secure-asserts).

|||
|-|-|
|TypeName|SecureAsserts|
|Identificador de comprobación|CA2106|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método valida un permiso y no se realiza ninguna comprobación de seguridad en el llamador.

## <a name="rule-description"></a>Descripción de la regla
 Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código. Un recorrido de pila de seguridad se detiene cuando se impone un permiso de seguridad. Si valida un permiso sin realizar ninguna comprobación en el llamador, el llamador podría ejecutar código indirectamente mediante el uso de sus permisos. Aserciones sin comprobaciones de seguridad están permitidos únicamente cuando esté seguro de que la aserción no se puede usar de manera perjudicial. Una aserción es inofensiva si el código que se llama es inocuo, o los usuarios no pueden pasar información arbitraria al código que llama.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregar una petición de seguridad para el método o su tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de revisar cuidadosamente la seguridad.

## <a name="see-also"></a>Vea también
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Instrucciones de codificación segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)



