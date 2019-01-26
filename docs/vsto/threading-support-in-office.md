---
title: Compatibilidad del subprocesamiento en Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0dae42e2648af1212a676c8956122b4fde072d20
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866131"
---
# <a name="threading-support-in-office"></a>Compatibilidad del subprocesamiento en Office
  Este artículo proporciona información acerca de subprocesamientos en el modelo de objetos de Microsoft Office. El modelo de objetos de Office no es seguro para subprocesos, pero es posible trabajar con varios subprocesos en una solución de Office. Las aplicaciones de Office son servidores de modelo de objetos componentes (COM). COM permite a los clientes llamar a los servidores COM en subprocesos arbitrarios. Para los servidores COM que no son seguros para subprocesos, COM ofrece un mecanismo para serializar llamadas simultáneas de modo que sólo un subproceso lógico que se ejecuta en el servidor en cualquier momento. Este mecanismo se conoce como el modelo de contenedor uniproceso (STA). Dado que las llamadas se serializan, los autores de llamadas podrían bloquearse durante períodos de tiempo mientras el servidor está ocupado o controlando otras llamadas en un subproceso en segundo plano.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Conocimientos necesarios al utilizar varios subprocesos  
 Para trabajar con varios subprocesos, debe tener al menos un conocimiento básico de los siguientes aspectos de multithreading:  
  
- API de Windows  
  
- COM conceptos multiproceso  
  
- simultaneidad  
  
- Sincronización  
  
- El cálculo de referencias  
  
  Para obtener información general sobre multithreading, vea [Managed threading](/dotnet/standard/threading/).  
  
  Office se ejecuta en el STA principal. Comprender las implicaciones de esto hace posible aprender a usar varios subprocesos con Office.  
  
## <a name="basic-multithreading-scenario"></a>Escenario básico de subprocesamiento múltiple  
 Código en soluciones de Office siempre se ejecuta en el subproceso de interfaz de usuario principal. Es posible que desee suavizar el rendimiento de la aplicación mediante la ejecución de una tarea independiente en un subproceso en segundo plano. El objetivo es completar dos tareas aparentemente a la vez en lugar de una tarea seguida por otro, lo que debe dar como resultado una ejecución más uniforme (la razón principal para usar varios subprocesos). Por ejemplo, es posible que tenga el código de evento en el subproceso principal de la interfaz de usuario de Excel y en un subproceso en segundo plano podría ejecutar una tarea que recopila datos de un servidor y actualiza las celdas de la interfaz de usuario de Excel con los datos del servidor.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Subprocesos en segundo plano que llaman al modelo de objetos de Office  
 Cuando un subproceso en segundo plano realiza una llamada a la aplicación de Office, la llamada se serializa automáticamente a través del límite STA. Sin embargo, no hay ninguna garantía de que la aplicación de Office puede controlar la llamada al tiempo que hace que el subproceso en segundo plano. Hay varias causas posibles:  
  
1. La aplicación de Office debe suministrar mensajes para la llamada tenga la oportunidad de ENTRAR. Si está realizando con mucha actividad de procesamiento sin producir esto podría llevar tiempo.  
  
2. Si otro subproceso lógico ya está en el apartamento, no se puede escribir el nuevo subproceso. Esto suele ocurrir cuando un subproceso lógico entra en la aplicación de Office y, a continuación, realiza una llamada reentrante al apartamento del llamador. La aplicación se bloquea en espera para que devuelva la llamada.  
  
3. Excel podría estar en un estado de modo que no puede manejar inmediatamente una llamada entrante. Por ejemplo, la aplicación de Office podría estar mostrando un cuadro de diálogo modal.  
  
   Para las posibilidades 2 y 3, COM proporciona el [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) interfaz. Si implementa el servidor, escriba todas las llamadas a través de la [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) método. Para la posibilidad 2, las llamadas se rechazan automáticamente. Para la posibilidad de 3, el servidor puede rechazar la llamada, dependiendo de las circunstancias. Si se rechaza la llamada, el llamador debe decidir qué hacer. Normalmente, el implementa llamador [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), en cuyo caso sería notificado del rechazo por el [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) método.  
  
   Sin embargo, en el caso de las soluciones creadas con las herramientas de desarrollo de Office en Visual Studio, la interoperabilidad COM convierte todas las llamadas rechazadas para una <xref:System.Runtime.InteropServices.COMException> ("el filtro de mensaje indica que la aplicación está ocupada"). Cada vez que llamar a un modelo de objetos en un subproceso en segundo plano, debe estar preparado para controlar esta excepción. Normalmente, esto implica volver a intentar para una determinada cantidad de tiempo y, a continuación, mostrar un cuadro de diálogo. Sin embargo, puede crear también el subproceso en segundo plano como STA y, a continuación, registrar un filtro de mensajes de ese subproceso para controlar este caso.  
  
## <a name="start-the-thread-correctly"></a>El subproceso se inicia correctamente  
 Cuando se crea un nuevo subproceso STA, establezca el estado del apartamento en STA antes de iniciar el subproceso. En el ejemplo de código siguiente se muestra cómo utilizar este recurso.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Para obtener más información, consulte [Managed threading best practices](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Formularios no modales  
 Una forma no modal permite a algún tipo de interacción con la aplicación mientras se muestra el formulario. El usuario interactúa con el formulario y el formulario interactúa con la aplicación sin cerrar. El modelo de objetos de Office es compatible con los formularios no modales administrados; Sin embargo, no se debe usar en un subproceso en segundo plano.  
  
## <a name="see-also"></a>Vea también  
 [Subprocesamiento administrado](/dotnet/standard/threading/)  
 [Subprocesamiento (C#)](/dotnet/csharp/programming-guide/concepts/threading/index) [subprocesamiento (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Use subprocesos y subprocesamiento](/dotnet/standard/threading/using-threads-and-threading)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
