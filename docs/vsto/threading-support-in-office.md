---
title: Compatibilidad del subprocesamiento en Office | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3383e3767c97efad9177f0e361524137ea5d66a8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="threading-support-in-office"></a>Compatibilidad del subprocesamiento en Office
  Este tema proporciona información sobre cómo se admite el subprocesamiento en el modelo de objetos de Microsoft Office. El modelo de objetos de Office no es seguro para subprocesos, pero es posible trabajar con varios subprocesos en una solución de Office. Las aplicaciones de Office son servidores de modelo de objetos componentes (COM). COM permite a los clientes llamar a servidores COM en subprocesos arbitrarios. Para los servidores COM que no son seguros para subprocesos, COM proporciona un mecanismo para serializar llamadas simultáneas para que sólo un subproceso lógico que se ejecuta en el servidor en cualquier momento. Este mecanismo se conoce como el modelo de contenedor uniproceso (STA). Porque las llamadas se serializan, los llamadores pueden quedar bloqueados durante períodos de tiempo mientras el servidor está ocupado o controlando otras llamadas en un subproceso en segundo plano.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Conocimientos necesarios al utilizar varios subprocesos  
 Para trabajar con varios subprocesos, debe tener al menos un conocimiento básico de los siguientes aspectos de multithreading:  
  
-   API de Windows  
  
-   COM conceptos multiproceso  
  
-   simultaneidad  
  
-   Sincronización  
  
-   el cálculo de referencias  
  
 Para obtener información general sobre multithreading, vea [Managed Threading](/dotnet/standard/threading/).  
  
 Office se ejecuta en el STA principal. Comprender las implicaciones de este permite entender cómo utilizar varios subprocesos con Office.  
  
## <a name="basic-multithreading-scenario"></a>Escenario de Multithreading básico  
 Código en soluciones de Office siempre se ejecuta en el subproceso de interfaz de usuario principal. Puede suavizar el rendimiento de la aplicación mediante la ejecución de una tarea independiente en un subproceso en segundo plano. El objetivo es completar dos tareas aparentemente al mismo tiempo en lugar de una tarea seguida por el otro, lo que dará lugar a una ejecución más uniforme (es decir, la razón principal para utilizar varios subprocesos). Por ejemplo, es posible que tenga el código de evento en el subproceso principal de la interfaz de usuario de Excel y en un subproceso en segundo plano puede ejecutar una tarea que recopila datos de un servidor y actualiza las celdas de la interfaz de usuario de Excel con los datos del servidor.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Subprocesos en segundo plano que llaman al modelo de objetos de Office  
 Cuando un subproceso en segundo plano realiza una llamada a la aplicación de Office, la llamada se realizará a través del límite STA. Sin embargo, no hay ninguna garantía de que la aplicación de Office pueda controlar la llamada en el momento en que hace que el subproceso en segundo plano. Hay varias causas posibles:  
  
1.  La aplicación de Office debe suministrar mensajes para que la llamada tenga la oportunidad de especificar. Si está muy ocupado en procesamientos sin resultados, esto puede llevar tiempo.  
  
2.  Si otro subproceso lógico ya está en el apartamento, no se puede escribir el nuevo subproceso. Esto suele ocurrir cuando un subproceso lógico entra en la aplicación de Office y, a continuación, realiza una llamada reentrante al apartamento del llamador. La aplicación se bloquea en espera para que devuelva la llamada.  
  
3.  Excel podría estar en un estado de modo que no se puede controlar inmediatamente una llamada entrante. Por ejemplo, la aplicación de Office podría estar mostrando un cuadro de diálogo modal.  
  
 Para las posibilidades 2 y 3, COM proporciona el [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248) interfaz. Si el servidor la implementa, todas las llamadas entran a través de la [HandleIncomingCall](http://msdn.microsoft.com/en-us/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be) método. Para la posibilidad 2, las llamadas se rechazan automáticamente. Para la posibilidad 3, el servidor puede rechazar la llamada, dependiendo de las circunstancias. Si se rechaza la llamada, el llamador debe decidir qué hacer. Normalmente, el implementa llamador [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248), en cuyo caso sería notificado del rechazo por el [RetryRejectedCall](http://msdn.microsoft.com/en-us/3f800819-2a21-4e46-ad15-f9594fac1a3d) método.  
  
 Sin embargo, en el caso de soluciones creadas con las herramientas de desarrollo de Office en Visual Studio, la interoperabilidad COM convierte todas las llamadas rechazadas a un <xref:System.Runtime.InteropServices.COMException> ("el filtro de mensajes indicó que la aplicación está ocupada"). Siempre que se realice un modelo de objetos llamar en un subproceso en segundo plano, debe estar preparado para controlar esta excepción. Normalmente, esto implica volver a intentarlo durante un período de tiempo y, a continuación, mostrar un cuadro de diálogo. Sin embargo, también puede crear el subproceso en segundo plano como STA y, a continuación, registrar un filtro de mensajes para ese subproceso controlar este caso.  
  
## <a name="starting-the-thread-correctly"></a>Iniciar correctamente el subproceso  
 Cuando se crea un nuevo subproceso STA, establezca el estado del apartamento en STA antes de iniciar el subproceso. En el ejemplo de código siguiente se muestra cómo utilizar este recurso.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Para obtener más información, consulte [Managed Threading Best Practices](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Formularios no modales  
 Un formulario no modal permite a cierto tipo de interacción con la aplicación mientras se muestra el formulario. El usuario interactúa con el formulario y el formulario interactúa con la aplicación sin cerrar. El modelo de objetos de Office es compatible con formularios no modales administrados; Sin embargo, no debe utilizar en un subproceso en segundo plano.  
  
## <a name="see-also"></a>Vea también  
 [Subprocesamiento administrado](/dotnet/standard/threading/)  
 [Subprocesamiento (C#)](/dotnet/csharp/programming-guide/concepts/threading/index) [subprocesamiento (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Uso de subprocesos y subprocesamiento](/dotnet/standard/threading/using-threads-and-threading)   
 [Diseño y creación de soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  