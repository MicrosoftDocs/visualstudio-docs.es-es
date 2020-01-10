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
ms.openlocfilehash: 6a2ed905f8291bf503217239cc287c50b970572f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851725"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Evitar llamar a métodos problemáticos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|Identificador de comprobación|CA2001|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un miembro llama a un método potencialmente peligroso o problemático.

## <a name="rule-description"></a>Descripción de la regla
 Evite realizar llamadas a métodos innecesarias y potencialmente peligrosas.

 Una infracción de esta regla se produce cuando un miembro llama a uno de los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Llamando a GC. Collect puede afectar significativamente al rendimiento de la aplicación y rara vez es necesario. Para obtener más información, consulte la entrada de blog de [noticias muy interesantes de rendimiento de rico mariani's performance](https://blogs.msdn.com/ricom/archive/2004/11/29/271829.aspx) en MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend y Thread. resume están en desuso debido a su comportamiento imprevisible.  Use otras clases en el espacio de nombres <xref:System.Threading>, como <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>y <xref:System.Threading.Semaphore> para sincronizar los subprocesos o proteger los recursos.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|El método DangerousGetHandle supone un riesgo para la seguridad porque puede devolver un identificador no válido. Vea los métodos <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> y <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> para obtener más información sobre cómo usar el método DangerousGetHandle de forma segura.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Estos métodos pueden cargar ensamblados desde ubicaciones inesperadas. Por ejemplo, vea [las entradas de](https://blogs.msdn.com/suzcook/archive/2003/09/19/loadfile-vs-loadfrom.aspx) blog sobre las notas de .net CLR de Suzanne Cook [en el](https://blogs.msdn.com/suzcook/archive/2003/05/29/57143.aspx) sitio web de MSDN para obtener información sobre los métodos que cargan los ensamblados.|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) (Ole32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (Ole32)|En el momento en que el código de usuario empieza a ejecutarse en un proceso administrado, es demasiado tarde para llamar a CoSetProxyBlanket de forma confiable. El Common Language Runtime (CLR) realiza acciones de inicialización que pueden impedir que los usuarios P/Invoke se ejecuten correctamente.<br /><br /> Si tiene que llamar a CoSetProxyBlanket para una aplicación administrada, se recomienda que inicie el proceso con un ejecutable de código nativo (C++), llame a CoSetProxyBlanket en el código nativo y, a continuación, inicie la aplicación de código administrado en proceso. (Asegúrese de especificar un número de versión en tiempo de ejecución).|

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite o reemplace la llamada al método peligroso o problemático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Solo debe suprimir los mensajes de esta regla cuando no estén disponibles alternativas al método problemático.

## <a name="see-also"></a>Vea también
 [Advertencias de confiabilidad](../code-quality/reliability-warnings.md)
