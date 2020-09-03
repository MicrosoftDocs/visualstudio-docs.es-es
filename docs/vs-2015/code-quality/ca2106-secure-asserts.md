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
ms.openlocfilehash: eb0e097c2f13fa9d9279a5f3e9761a53cb6e4b1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547750"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Proteger las aserciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|SecureAsserts|
|Identificador de comprobación|CA2106|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método valida un permiso y no se realiza ninguna comprobación de seguridad en el llamador.

## <a name="rule-description"></a>Descripción de la regla
 Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código. Un recorrido de pila de seguridad se detiene cuando se impone un permiso de seguridad. Si valida un permiso sin realizar ninguna comprobación en el autor de la llamada, el llamador podría ejecutar el código indirectamente mediante sus permisos. Las aserciones sin comprobaciones de seguridad solo se permiten cuando se está seguro de que la aserción no se puede usar de forma dañina. Una aserción es inocua si el código al que se llama es inofensivo o los usuarios no pueden pasar información arbitraria al código al que llama.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue una solicitud de seguridad al método o a su tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de una revisión cuidadosa de la seguridad.

## <a name="see-also"></a>Consulte también
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
