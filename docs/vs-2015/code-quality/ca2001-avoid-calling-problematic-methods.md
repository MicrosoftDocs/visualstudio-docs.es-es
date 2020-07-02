---
title: 'CA2001: evitar llamar a métodos problemáticos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba64c27cde5f335f32cca362417078a5c9ed13e3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538585"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Evitar llamar a métodos problemáticos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|Identificador de comprobación|CA2001|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un miembro llama a un método potencialmente peligroso o problemático.

## <a name="rule-description"></a>Descripción de la regla
 Evite realizar llamadas a métodos innecesarias y potencialmente peligrosas.

 Una infracción de esta regla se produce cuando un miembro llama a uno de los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Llamando a GC. Collect puede afectar significativamente al rendimiento de la aplicación y rara vez es necesario. Para obtener más información, consulte la entrada de blog de [noticias muy interesantes de rendimiento de rico mariani's performance](https://docs.microsoft.com/archive/blogs/ricom/when-to-call-gc-collect) en MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend y Thread. resume están en desuso debido a su comportamiento imprevisible.  Use otras clases en el <xref:System.Threading> espacio de nombres, como <xref:System.Threading.Monitor> , <xref:System.Threading.Mutex> , y <xref:System.Threading.Semaphore> para sincronizar los subprocesos o proteger los recursos.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|El método DangerousGetHandle supone un riesgo para la seguridad porque puede devolver un identificador no válido. Vea los <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> métodos y <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> para obtener más información sobre cómo usar el método DangerousGetHandle de forma segura.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Estos métodos pueden cargar ensamblados desde ubicaciones inesperadas. Por ejemplo, vea [las entradas de](https://docs.microsoft.com/archive/blogs/suzcook/loadfile-vs-loadfrom) blog sobre las notas de .net CLR de Suzanne Cook [en el](https://docs.microsoft.com/archive/blogs/suzcook/choosing-a-binding-context) sitio web de MSDN para obtener información sobre los métodos que cargan los ensamblados.|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) (ole32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (ole32)|En el momento en que el código de usuario empieza a ejecutarse en un proceso administrado, es demasiado tarde para llamar a CoSetProxyBlanket de forma confiable. El Common Language Runtime (CLR) realiza acciones de inicialización que pueden impedir que los usuarios P/Invoke se ejecuten correctamente.<br /><br /> Si tiene que llamar a CoSetProxyBlanket para una aplicación administrada, se recomienda iniciar el proceso con un ejecutable de código nativo (C++), llamar a CoSetProxyBlanket en el código nativo y, a continuación, iniciar la aplicación de código administrado en proceso. (Asegúrese de especificar un número de versión en tiempo de ejecución).|

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite o reemplace la llamada al método peligroso o problemático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Solo debe suprimir los mensajes de esta regla cuando no estén disponibles alternativas al método problemático.

## <a name="see-also"></a>Consulte también
 [Advertencias de confiabilidad](../code-quality/reliability-warnings.md)
