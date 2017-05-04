---
title: "Compatibilidad del subprocesamiento en Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "varios subprocesos [desarrollo de Office en Visual Studio]"
  - "modelos de objeto [desarrollo de Office en Visual Studio], compatibilidad del subprocesamiento"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], compatibilidad del subprocesamiento"
  - "subprocesos [desarrollo de Office en Visual Studio]"
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Compatibilidad del subprocesamiento en Office
  En este tema se proporciona información sobre compatibilidad de subprocesamientos en el modelo de objetos de Microsoft Office.  El modelo de objetos de Office no es seguro para subprocesos, pero, en una solución de Office, es posible trabajar con varios subprocesos.  Las aplicaciones de Office son servidores de modelos de objetos componentes \(COM\).  Mediante COM, los clientes pueden llamar a servidores COM en subprocesos arbitrarios.  Para los servidores COM que no son seguros para subprocesos, COM proporciona un mecanismo para serializar llamadas simultáneas de modo que sólo se ejecute un subproceso lógico en el servidor en cada instante.  Este mecanismo se conoce como el modelo STA \(contenedor uniproceso\).  Dado que las llamadas se serializan, los llamadores pueden quedar bloqueados durante lapsos de tiempo mientras el servidor está ocupado o controlando otras llamadas en un subproceso de fondo.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Conocimientos necesarios al utilizar múltiples subprocesos  
 Para trabajar con varios subprocesos es necesario tener al menos un conocimiento básico de los siguientes aspectos de multithreading:  
  
-   APIs de Windows  
  
-   Conceptos multiproceso de COM  
  
-   Simultaneidad  
  
-   Sincronización  
  
-   Cálculo de referencias  
  
 Para obtener información general acerca de multithreading, vea [Multithreading in Components](../Topic/Multithreading%20in%20Components.md).  
  
 Office se ejecuta en el STA principal.  Entender las implicaciones que esto conlleva permite entender cómo utilizar varios subprocesos con Office.  
  
## Escenario de multithreading básico  
 El código de las soluciones de Office siempre se ejecuta en el subproceso de la interfaz de usuario principal.  Tal vez desee mejorar el rendimiento de la aplicación ejecutando una tarea independiente en un subproceso de fondo.  El objetivo consiste en completar ambas tareas aparentemente al mismo tiempo en lugar de una tarea tras otra, lo que tendría como resultado una ejecución más uniforme \(el motivo principal de usar múltiples subprocesos\).  Por ejemplo, podría tener el código de los eventos en el subproceso de la IU principal de Excel y, en un subproceso de fondo, ejecutar una tarea que recuperara datos de un servidor y actualizara las celdas en la IU de Excel con los datos obtenidos del servidor.  
  
## Subprocesos en segundo plano que realizan llamadas al modelo de objetos de Office  
 Cuando un subproceso de fondo realiza una llamada a la aplicación de Office, las referencias de la llamada se calculan automáticamente entre los límites del STA.  Sin embargo, no hay ninguna garantía de que la aplicación de Office pueda controlar la llamada en el momento en que el subproceso de fondo la realiza.  Hay varias posibilidades:  
  
1.  La aplicación de Office debe suministrar mensajes para que la llamada tenga la oportunidad de entrar.  Si está muy ocupado en procesamientos sin resultados, esto podría llevar tiempo.  
  
2.  Si otro subproceso lógico ya está en el apartamento, el nuevo subproceso no puede entrar.  Esto pasa a menudo cuando un subproceso lógico entra en la aplicación de Office y, a continuación, realiza una llamada que vuelve a entrar al apartamento del llamador.  La aplicación se bloquea a la espera de que se devuelva la llamada.  
  
3.  Excel podría estar en un estado tal que no pudiera controlar inmediatamente una llamada entrante.  Por ejemplo, la aplicación de Office podría estar mostrando un cuadro de diálogo modal.  
  
 Para las posibilidades 2 y 3, COM proporciona la interfaz [IMessageFilter](http://msdn.microsoft.com/es-es/e12d48c0-5033-47a8-bdcd-e94c49857248).  Si el servidor la implementa, todas las llamadas entran a través del método [HandleIncomingCall](http://msdn.microsoft.com/es-es/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be).  Para la posibilidad 2, las llamadas se rechazan automáticamente.  Para la posibilidad 3, el servidor puede rechazar la llamada, dependiendo de las circunstancias.  Si se rechaza la llamada, el llamador debe decidir qué hacer.  Normalmente, el llamador implementa [IMessageFilter](http://msdn.microsoft.com/es-es/e12d48c0-5033-47a8-bdcd-e94c49857248), en cuyo caso sería notificado del rechazo por el método [RetryRejectedCall](http://msdn.microsoft.com/es-es/3f800819-2a21-4e46-ad15-f9594fac1a3d).  
  
 Sin embargo, en el caso de las soluciones creadas mediante las herramientas de desarrollo de Office en Visual Studio, la interoperabilidad COM convierte todas las llamadas rechazadas en <xref:System.Runtime.InteropServices.COMException> \("El filtro de mensaje indicó que la aplicación está ocupada"\).  Siempre que se realice una llamada del modelo de objetos en un subproceso de fondo, se debe estar preparado para controlar esta excepción.  Normalmente, esto implica tener que reintentarlo una cierta cantidad de veces y mostrar después un cuadro de diálogo.  Sin embargo, también puede crear el subproceso de fondo como STA y, a continuación, registrar un filtro de mensajes para ese subproceso para controlar este caso.  
  
## Iniciar correctamente el subproceso  
 Cuando cree un nuevo subproceso STA, establezca el estado de tipo apartamento en STA antes de iniciar el subproceso.  En el ejemplo de código siguiente se muestra cómo hacerlo.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/ThisWorkbook.vb#5)]  
  
 Para obtener más información, vea [Managed Threading Best Practices](../Topic/Managed%20Threading%20Best%20Practices.md).  
  
## Formularios no modales  
 Un formulario no modal permite cierto tipo de interacción con la aplicación mientras se muestra el formulario.  El usuario interactúa con el formulario y el formulario interactúa con la aplicación sin cerrarse.  El modelo de objetos de Office admite el uso de formularios no modales administrados; sin embargo, no se deben usar en un subproceso de fondo.  
  
## Vea también  
 [Multithreading in Components](../Topic/Multithreading%20in%20Components.md)   
 [Managed Threading](../Topic/Managed%20Threading.md)   
 [Subprocesamiento &#40;C&#35; y Visual Basic&#41;](../Topic/Threading%20(C%23%20and%20Visual%20Basic).md)   
 [Using Threads and Threading](../Topic/Using%20Threads%20and%20Threading.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  