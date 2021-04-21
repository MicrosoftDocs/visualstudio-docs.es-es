---
title: Compatibilidad con subprocesos en Office
description: El subprocesamiento se admite en el Microsoft Office de objetos. El modelo de objetos de Office no es seguro para subprocesos, pero puede trabajar con varios subprocesos en una solución de Office.
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
ms.openlocfilehash: dce8bb0667cecbe073c734595d341f9c7b7ccac9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826088"
---
# <a name="threading-support-in-office"></a>Compatibilidad con subprocesos en Office
  En este artículo se proporciona información sobre cómo se admite el subprocesamiento en el Microsoft Office de objetos. El modelo de objetos de Office no es seguro para subprocesos, pero es posible trabajar con varios subprocesos en una solución de Office. Las aplicaciones de Office son servidores de Modelo de objetos componentes (COM). COM permite a los clientes llamar a servidores COM en subprocesos arbitrarios. En el caso de los servidores COM que no son seguros para subprocesos, COM proporciona un mecanismo para serializar llamadas simultáneas para que solo se ejecute un subproceso lógico en el servidor en cualquier momento. Este mecanismo se conoce como modelo de apartamento de un solo subproceso (STA). Dado que las llamadas se serializan, es posible que los llamadores se bloqueen durante períodos de tiempo mientras el servidor está ocupado o está controlando otras llamadas en un subproceso en segundo plano.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Conocimiento necesario al usar varios subprocesos
 Para trabajar con varios subprocesos, debe tener al menos conocimientos básicos de los siguientes aspectos del multithreading:

- API de Windows

- Conceptos multiproceso com

- Simultaneidad

- Synchronization

- Marshaling

  Para obtener información general sobre el multithreading, vea [Subprocesos administrados.](/dotnet/standard/threading/)

  Office se ejecuta en el STA principal. Comprender las implicaciones de esto permite comprender cómo usar varios subprocesos con Office.

## <a name="basic-multithreading-scenario"></a>Escenario básico de multithreading
 El código de las soluciones de Office siempre se ejecuta en el subproceso principal de la interfaz de usuario. Es posible que desee suavizar el rendimiento de la aplicación mediante la ejecución de una tarea independiente en un subproceso en segundo plano. El objetivo es completar dos tareas aparentemente a la vez en lugar de una tarea seguida de la otra, lo que debería dar lugar a una ejecución más fluida (el motivo principal para usar varios subprocesos). Por ejemplo, podría tener el código de evento en el subproceso principal de la interfaz de usuario de Excel y, en un subproceso en segundo plano, podría ejecutar una tarea que recopila datos de un servidor y actualiza las celdas de la interfaz de usuario de Excel con los datos del servidor.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Subprocesos en segundo plano que llaman al modelo de objetos de Office
 Cuando un subproceso en segundo plano realiza una llamada a la aplicación de Office, la llamada se serializa automáticamente a través del límite sta. Sin embargo, no hay ninguna garantía de que la aplicación de Office pueda controlar la llamada en el momento en que el subproceso en segundo plano la realiza. Hay varias causas posibles:

1. La aplicación de Office debe enviar mensajes para que la llamada tenga la oportunidad de escribir. Si está realizando un procesamiento pesado sin producir esto, podría tardar tiempo.

2. Si otro subproceso lógico ya está en el contenedor, el nuevo subproceso no puede entrar. Esto suele ocurrir cuando un subproceso lógico entra en la aplicación de Office y, a continuación, realiza una llamada reentrante al apartamento del autor de la llamada. La aplicación está bloqueada a la espera de que se devuelva esa llamada.

3. Excel podría estar en un estado tal que no pueda controlar inmediatamente una llamada entrante. Por ejemplo, la aplicación de Office podría mostrar un cuadro de diálogo modal.

   Para las posibilidades 2 y 3, COM proporciona la [interfaz IMessageFilter.](/windows/desktop/api/objidl/nn-objidl-imessagefilter) Si el servidor lo implementa, todas las llamadas entran a través del [método HandleIncomingCall.](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) En la posibilidad 2, las llamadas se rechazan automáticamente. Para la posibilidad 3, el servidor puede rechazar la llamada, en función de las circunstancias. Si se rechaza la llamada, el autor de la llamada debe decidir qué hacer. Normalmente, el autor de la llamada implementa [IMessageFilter,](/windows/desktop/api/objidl/nn-objidl-imessagefilter)en cuyo caso el método [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) le notificaría el rechazo.

   Sin embargo, en el caso de las soluciones creadas mediante las herramientas de desarrollo de Office en Visual Studio, la interoperabilidad COM convierte todas las llamadas rechazadas en un ("El filtro de mensaje indica que la aplicación está <xref:System.Runtime.InteropServices.COMException> ocupada"). Siempre que realice una llamada de modelo de objetos en un subproceso en segundo plano, debe estar preparado para controlar esta excepción. Normalmente, esto implica reintentar durante una determinada cantidad de tiempo y, a continuación, mostrar un cuadro de diálogo. Sin embargo, también puede crear el subproceso en segundo plano como STA y, a continuación, registrar un filtro de mensaje para que ese subproceso controle este caso.

## <a name="start-the-thread-correctly"></a>Iniciar el subproceso correctamente
 Cuando cree un subproceso STA, establezca el estado del apartamento en STA antes de iniciar el subproceso. En el ejemplo de código siguiente se muestra cómo utilizar este recurso.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs" id="Snippet5":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb" id="Snippet5":::

 Para obtener más información, consulte [Procedimientos recomendados para subprocesos administrados.](/dotnet/standard/threading/managed-threading-best-practices)

## <a name="modeless-forms"></a>Formularios modelados
 Un formulario modelado permite algún tipo de interacción con la aplicación mientras se muestra el formulario. El usuario interactúa con el formulario y el formulario interactúa con la aplicación sin cerrarse. El modelo de objetos de Office admite formularios modelados administrados; sin embargo, no deben usarse en un subproceso en segundo plano.

## <a name="see-also"></a>Consulte también
- [Subprocesamiento (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Subprocesamiento (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Uso de subprocesos y subprocesos](/dotnet/standard/threading/using-threads-and-threading)
- [Diseño y creación de soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
