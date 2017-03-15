---
title: "CA2001: Evitar llamar a m&#233;todos problem&#225;ticos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2001"
  - "AvoidCallingProblematicMethods"
helpviewer_keywords: 
  - "CA2001"
  - "AvoidCallingProblematicMethods"
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2001: Evitar llamar a m&#233;todos problem&#225;ticos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidCallingProblematicMethods|  
|Identificador de comprobación|CA2001|  
|Categoría|Microsoft.Reliability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un miembro llama a un método potencialmente peligroso o problemático.  
  
## Descripción de la regla  
 Evite realizar llamadas a métodos potencialmente peligrosas e innecesarias.  
  
 Esta regla se infringe cuando un miembro llama a uno de los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Llamar a GC.Collect puede afectar al rendimiento de la aplicación significativamente y rara vez es necesario.  Para obtener más información, vea [Curiosidades de rendimiento de Enriquecido Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) la entrada de blog en MSDN.|  
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend y Thread.Resume han quedado en desuso debido a su comportamiento impredecible.  Utilice otras clases del espacio de nombres <xref:System.Threading>, como <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex%2C>, <xref:System.Threading.Mutex> y <xref:System.Threading.Semaphore> para sincronizar los subprocesos o proteger los recursos.|  
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|El método DangerousGetHandle supone un riesgo para la seguridad porque puede devolver un controlador que es no válido.  Vea los métodos <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> y <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> para obtener más información sobre cómo utilizar el método DangerousGetHandle de forma segura.|  
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Estos métodos pueden cargar ensamblados desde ubicaciones inesperadas.  Por ejemplo, vea elementos [LoadFile con LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) de blog notas de .NET CLR de Susana Cook y [Elegir un contexto de enlace](http://go.microsoft.com/fwlink/?LinkId=164451) en el sitio web de MSDN para obtener información sobre los métodos que cargan los ensamblados.|  
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) \(Ole32\)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) \(Ole32\)|Cuando el código de usuario comienza a ejecutarse en un proceso administrado, es demasiado tarde para llamar de forma confiable a CoSetProxyBlanket.  Common Language Runtime \(CLR\) toma medidas de inicialización que pueden impedir que los usuarios usen P\/Invoke con éxito.<br /><br /> Si necesita llamar a CoSetProxyBlanket para una aplicación administrada, se recomienda que inicie el proceso mediante un ejecutable de código nativo \(C\+\+\), llame a CoSetProxyBlanket en el código nativo y, a continuación, inicie la aplicación de código administrado en proceso. \(Asegúrese de especificar el número de versión del motor en tiempo de ejecución.\)|  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite o reemplace la llamada al método peligroso o problemático.  
  
## Cuándo suprimir advertencias  
 Solo debería suprimir los mensajes de esta regla cuando no haya otra alternativa disponible al método problemático.  
  
## Vea también  
 [Advertencias de confiabilidad](../code-quality/reliability-warnings.md)