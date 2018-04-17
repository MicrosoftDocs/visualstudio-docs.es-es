---
title: 'CA2001: Evitar llamar a métodos problemáticos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d26009b91e8459c6f17e717fae060d1f857e8fe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Evitar llamar a métodos problemáticos
|||  
|-|-|  
|TypeName|AvoidCallingProblematicMethods|  
|Identificador de comprobación|CA2001|  
|Categoría|Microsoft.Reliability|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un miembro llama a un método potencialmente peligroso o problemático.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Evitar la realización de llamadas a métodos potencialmente peligrosas e innecesarias.  
  
 Cuando un miembro llama a uno de los métodos siguientes, se produce una infracción de esta regla.  
  
|Método|Descripción|  
|------------|-----------------|  
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Llamar a GC. Collect puede afectar significativamente al rendimiento de la aplicación y no suele ser necesario. Para obtener más información, consulte el [curiosidades sobre rendimiento de Rico Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) entrada de blog en MSDN.|  
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend y Thread.Resume han quedado en desuso debido a su comportamiento impredecible.  Utilice otras clases de la <xref:System.Threading> espacio de nombres, como <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, <xref:System.Threading.Mutex>, y <xref:System.Threading.Semaphore> para sincronizar los subprocesos o proteger los recursos.|  
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|El método DangerousGetHandle supone un riesgo de seguridad porque puede devolver un identificador que no es válido. Consulte la <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> y <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> métodos para obtener más información acerca de cómo usar el método DangerousGetHandle de forma segura.|  
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Estos métodos pueden cargar ensamblados desde ubicaciones inesperadas. Por ejemplo, vea las entradas de blog de .NET CLR Notes del Suzanne Cook [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) y [elegir un contexto de enlace](http://go.microsoft.com/fwlink/?LinkId=164451) en el sitio Web de MSDN para obtener información acerca de los métodos que cargan ensamblados.|  
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|En el momento en que el código de usuario empieza a ejecutarse en un proceso administrado, es demasiado tarde para llamar de forma confiable a CoSetProxyBlanket. Common language runtime (CLR) realiza acciones de inicialización que pueden impedir que los usuarios P/Invoke correctamente.<br /><br /> Si tiene que llamar a CoSetProxyBlanket para una aplicación administrada, se recomienda que inicie el proceso mediante un archivo ejecutable de código nativo (C++), llame a CoSetProxyBlanket en el código nativo y, a continuación, inicie la aplicación de código administrado en proceso. (Asegúrese de especificar un número de versión en tiempo de ejecución).|  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite o reemplace la llamada al método peligroso o problemático.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Se deben suprimir los mensajes de esta regla sólo cuando no hay alternativas al método problemático están disponibles.  
  
## <a name="see-also"></a>Vea también  
 [Advertencias de confiabilidad](../code-quality/reliability-warnings.md)