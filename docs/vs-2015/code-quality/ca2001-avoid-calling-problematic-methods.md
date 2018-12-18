---
title: 'CA2001: Evitar llamar a métodos problemáticos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ddc96857cf0c3c54472eded5545ca0f328eba213
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902794"
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
 Evite realizar llamadas a métodos potencialmente peligrosas e innecesarias.

 Cuando un miembro llama a uno de los métodos siguientes, se produce una infracción de esta regla.

|Método|Descripción|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Una llamada a GC. Collect puede afectar significativamente al rendimiento de la aplicación y no suele ser necesario. Para obtener más información, consulte el [Performance Tidbits de Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) entrada de blog en MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend y Thread.Resume han quedado en desuso debido a un comportamiento impredecible.  Use otras clases en el <xref:System.Threading> espacio de nombres, como <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, y <xref:System.Threading.Semaphore> para sincronizar los subprocesos o proteger recursos.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|El método DangerousGetHandle plantea un riesgo de seguridad porque puede devolver un identificador que no es válido. Consulte la <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> y <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> métodos para obtener más información acerca de cómo usar el método DangerousGetHandle de forma segura.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Estos métodos pueden cargar ensamblados desde ubicaciones inesperadas. Por ejemplo, ver entradas de blog de .NET CLR notas de Suzanne Cook [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) y [elegir un contexto de enlace](http://go.microsoft.com/fwlink/?LinkId=164451) en el sitio Web de MSDN para obtener información acerca de los métodos que cargan los ensamblados.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|En el momento en que el código de usuario comienza a ejecutarse en un proceso administrado, es demasiado tarde para llamar de forma confiable a CoSetProxyBlanket. Common language runtime (CLR) realiza las acciones de inicialización que pueden impedir que los usuarios de P/Invoke que sigue.<br /><br /> Si es necesario llamar a CoSetProxyBlanket para una aplicación administrada, se recomienda iniciar el proceso mediante el uso de un archivo ejecutable de código nativo (C++), llame a CoSetProxyBlanket en el código nativo y, a continuación, inicie la aplicación de código administrado en proceso. (Asegúrese de especificar un número de versión en tiempo de ejecución).|

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite o reemplace la llamada al método peligroso o problemático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Se deben suprimir los mensajes de esta regla solo cuando no hay alternativas al método problemático están disponibles.

## <a name="see-also"></a>Vea también
 [Advertencias de confiabilidad](../code-quality/reliability-warnings.md)



