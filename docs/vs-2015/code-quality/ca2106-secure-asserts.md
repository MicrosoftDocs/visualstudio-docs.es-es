---
title: 'CA2106: proteger aserciones | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1f333478c952db74fa6a9482cdad91ce6a858301
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665998"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Asegurar aserciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureAsserts|
|Identificador de comprobación|CA2106|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método valida un permiso y no se realiza ninguna comprobación de seguridad en el llamador.

## <a name="rule-description"></a>Descripción de la regla
 Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código. Un recorrido de pila de seguridad se detiene cuando se impone un permiso de seguridad. Si valida un permiso sin realizar ninguna comprobación en el autor de la llamada, el llamador podría ejecutar el código indirectamente mediante sus permisos. Las aserciones sin comprobaciones de seguridad solo se permiten cuando se está seguro de que la aserción no se puede usar de forma dañina. Una aserción es inocua si el código al que se llama es inofensivo o los usuarios no pueden pasar información arbitraria al código al que llama.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue una solicitud de seguridad al método o a su tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de una revisión cuidadosa de la seguridad.

## <a name="see-also"></a>Vea también
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
