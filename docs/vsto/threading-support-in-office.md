---
title: Compatibilidad de subprocesos en Office
description: Los subprocesos se admiten en el modelo de objetos de Microsoft Office. El modelo de objetos de Office no es seguro para subprocesos, pero puede funcionar con varios subprocesos en una solución de Office.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6fd35551c5c40494c169fb569113e3530f633a6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940805"
---
# <a name="threading-support-in-office"></a>Compatibilidad de subprocesos en Office
  En este artículo se proporciona información sobre cómo se admiten los subprocesos en el modelo de objetos de Microsoft Office. El modelo de objetos de Office no es seguro para subprocesos, pero es posible trabajar con varios subprocesos en una solución de Office. Las aplicaciones de Office son servidores del modelo de objetos componentes (COM). COM permite que los clientes llamen a los servidores COM en subprocesos arbitrarios. En el caso de los servidores COM que no son seguros para subprocesos, COM proporciona un mecanismo para serializar las llamadas simultáneas de modo que solo se ejecute un subproceso lógico en el servidor en cualquier momento. Este mecanismo se conoce como el modelo de contenedor uniproceso (STA). Dado que las llamadas se serializan, los llamadores pueden bloquearse durante períodos de tiempo mientras el servidor está ocupado o controlando otras llamadas en un subproceso en segundo plano.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Conocimiento necesario al usar varios subprocesos
 Para trabajar con varios subprocesos, debe tener al menos un conocimiento básico de los siguientes aspectos de multithreading:

- API de Windows

- Conceptos de COM multiproceso

- Simultaneidad

- Sincronización

- Marshaling

  Para obtener información general sobre el multithreading, vea [subprocesamiento administrado](/dotnet/standard/threading/).

  Office se ejecuta en el STA principal. Comprender las implicaciones de esto permite comprender cómo usar varios subprocesos con Office.

## <a name="basic-multithreading-scenario"></a>Escenario básico de multithreading
 El código en las soluciones de Office siempre se ejecuta en el subproceso principal de la interfaz de usuario. Es posible que quiera suavizar el rendimiento de la aplicación mediante la ejecución de una tarea independiente en un subproceso en segundo plano. El objetivo es completar dos tareas aparentemente a la vez en lugar de una tarea seguida de la otra, lo que debería dar lugar a una ejecución más fluida (la razón principal para usar varios subprocesos). Por ejemplo, podría tener el código de evento en el subproceso principal de la interfaz de usuario de Excel, y en un subproceso en segundo plano podría ejecutar una tarea que recopile datos de un servidor y actualice las celdas de la interfaz de usuario de Excel con los datos del servidor.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Subprocesos en segundo plano que llaman al modelo de objetos de Office
 Cuando un subproceso en segundo plano realiza una llamada a la aplicación de Office, se calculan las referencias de la llamada automáticamente a través del límite de STA. Sin embargo, no hay ninguna garantía de que la aplicación de Office pueda controlar la llamada en el momento en que el subproceso en segundo plano lo hace. Hay varias causas posibles:

1. La aplicación de Office debe bombear los mensajes para que la llamada tenga la oportunidad de entrar. Si se trata de un procesamiento intensivo sin producir esto, puede llevar tiempo.

2. Si ya hay otro subproceso lógico en el contenedor, el nuevo subproceso no puede entrar. Esto suele ocurrir cuando un subproceso lógico entra en la aplicación de Office y, a continuación, realiza una devolución de llamada reentrante al apartamento del llamador. La aplicación se bloquea en espera de que se devuelva la llamada.

3. Excel podría estar en un estado de modo que no pueda controlar inmediatamente una llamada entrante. Por ejemplo, la aplicación de Office podría mostrar un cuadro de diálogo modal.

   En el caso de las posibilidades 2 y 3, COM proporciona la interfaz [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) . Si el servidor lo implementa, todas las llamadas entran a través del método [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) . En la posibilidad 2, las llamadas se rechazan automáticamente. Para la posibilidad 3, el servidor puede rechazar la llamada, en función de las circunstancias. Si se rechaza la llamada, el llamador debe decidir qué hacer. Normalmente, el autor de la llamada implementa [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), en cuyo caso se le notificará el rechazo mediante el método [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) .

   Sin embargo, en el caso de las soluciones creadas con las herramientas de desarrollo de Office en Visual Studio, la interoperabilidad COM convierte todas las llamadas rechazadas a <xref:System.Runtime.InteropServices.COMException> ("el filtro de mensajes indicó que la aplicación está ocupada"). Siempre que realice una llamada del modelo de objetos en un subproceso en segundo plano, debe estar preparado para controlar esta excepción. Normalmente, esto implica volver a intentar durante un período de tiempo determinado y mostrar un cuadro de diálogo. Sin embargo, también puede crear el subproceso en segundo plano como STA y, a continuación, registrar un filtro de mensajes para ese subproceso para controlar este caso.

## <a name="start-the-thread-correctly"></a>Iniciar el subproceso correctamente
 Cuando cree un nuevo subproceso STA, establezca el estado del apartamento en STA antes de iniciar el subproceso. En el ejemplo de código siguiente se muestra cómo utilizar este recurso.

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 Para obtener más información, vea [procedimientos recomendados para el subprocesamiento administrado](/dotnet/standard/threading/managed-threading-best-practices).

## <a name="modeless-forms"></a>Formularios no modales
 Un formulario no modal permite algún tipo de interacción con la aplicación mientras se muestra el formulario. El usuario interactúa con el formulario y el formulario interactúa con la aplicación sin cerrarse. El modelo de objetos de Office admite formularios no modales administrados; sin embargo, no se deben usar en un subproceso en segundo plano.

## <a name="see-also"></a>Vea también
- [Subprocesamiento (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Subprocesamiento (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Usar subprocesos y subprocesos](/dotnet/standard/threading/using-threads-and-threading)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
