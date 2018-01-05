---
title: "CA1031: No capturar los tipos de excepción general | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1b11db50a4e6104c09a65ebe9e7616d223ef3ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: No capturar los tipos de excepción general
|||  
|-|-|  
|TypeName|DoNotCatchGeneralExceptionTypes|  
|Identificador de comprobación|CA1031|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Una excepción general como <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName> se captura en un `catch` instrucción o una cláusula catch general como `catch()` se utiliza.  
  
## <a name="rule-description"></a>Descripción de la regla  
 No se deben capturar excepciones generales.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, detectar una excepción más específica o vuelva a producir la excepción general como la última instrucción en el `catch` bloque.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Detectar tipos de excepción general puede ocultar problemas en tiempo de ejecución del usuario de la biblioteca y puede dificultar la depuración.  
  
> [!NOTE]
>  A partir de la [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], common language runtime (CLR) ya no entrega las excepciones de estado dañado que se producen en el sistema operativo y el código administrado, como las infracciones de acceso en [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], para ser controlada por el código administrado. Si desea compilar una aplicación en el [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] o versiones posteriores y mantener el control de excepciones de estado dañado, puede aplicar el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo al método que controla la excepción de estado dañado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe esta regla y un tipo que implementa correctamente el `catch` bloque.  
  
 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2200: Reiniciar para mantener los detalles de la pila](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)