---
title: "Pesta&#241;a General (Cuadro de di&#225;logo Propiedades del subproceso) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "subprocesos [Visual Studio], propiedades del subproceso"
  - "propiedades de subprocesos"
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pesta&#241;a General (Cuadro de di&#225;logo Propiedades del subproceso)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use este cuadro de diálogo para obtener más detalles de un subproceso concreto.  Para abrir este cuadro de diálogo, mueva el foco a una ventana de [vista de subprocesos](../debugger/threads-view.md) o abra la [vista Mensajes](../debugger/messages-view.md) y expanda un mensaje.  Seleccione cualquier nodo de subproceso en el árbol y, a continuación, elija **Propiedades** en el menú **Ver**.  
  
 El cuadro de diálogo **Propiedades del subproceso** contiene un panel, la pestaña **General**.  Están disponibles los siguientes parámetros de configuración:  
  
|Entry|Descripción|  
|-----------|-----------------|  
|**Nombre de módulo**|El nombre del módulo.|  
|**Id. de subproceso**|Identificador único de este subproceso.  Tenga en cuenta que los números de identificador de subproceso se reutilizan; sólo identifican un subproceso mientras dure.|  
|**Id. de proceso**|El identificador único del proceso.  Los números de identificador de procesos se reutilizan, por lo que identifican un proceso solamente mientras dure dicho proceso.  El tipo de objeto Process se crea cuando se ejecuta un programa.  Todos los subprocesos de un proceso comparten el mismo espacio de direcciones y tienen acceso a los mismos datos.  Elija este valor para ver las propiedades del identificador del proceso.|  
|**Estado subproc.**|Estado actual del subproceso.  Si un subproceso está en ejecución significa que está usando un procesador; un subproceso en espera está a punto de usarlo.  Un subproceso listo está a la espera de usar un procesador porque no hay ninguno libre.  Un subproceso en transición está esperando a que se ejecute un recurso; por ejemplo, espera a que la pila de ejecución se pagine desde el disco.  Un subproceso en espera no necesita el procesador porque está esperando a que se complete una operación periférica o a que quede libre un recurso.|  
|**Motivo de espera**|Solo es aplicable cuando el subproceso está en estado de espera.  Se usan pares de eventos para la comunicación con los subsistemas protegidos.|  
|**Tiempo de CPU**|Tiempo de CPU total gastado en este proceso y sus subprocesos.  Es igual a tiempo de usuario \+ tiempo con privilegios.|  
|**Tiempo de usuario**|Tiempo total que este subproceso ha estado ejecutando código en modo usuario.  Las aplicaciones se ejecutan en modo usuario, como sucede con subsistemas tales como el administrador de ventanas y el motor gráfico.|  
|**Tiempo con privil.**|Tiempo total que este subproceso ha estado ejecutando código en modo con privilegios.  Cuando se llama a un servicio de sistema de Windows, a menudo el servicio se ejecutará en modo con privilegios para obtener acceso a datos privados del sistema.  Estos datos están protegidos del acceso por parte de subprocesos que se ejecutan en modo usuario.  Las llamadas al sistema pueden ser explícitas o también implícitas, como cuando se produce un error de página o una interrupción.|  
|**Tiempo transcurrido**|Tiempo total \(en segundos\) que se ha ejecutado este subproceso.|  
|**Prioridad act.**|Prioridad dinámica actual de este subproceso.  Los subprocesos de un proceso pueden aumentar y disminuir su propia prioridad base con respecto a la prioridad base del proceso.|  
|**Prioridad base**|Prioridad base actual de este subproceso.|  
|**Dir. de inicio**|Dirección virtual de inicio para este subproceso.|  
|**User PC**|Contador de programa del usuario para el subproceso.|  
|**Cambios contexto**|Número de cambios de un subproceso a otro.  Los cambios de subproceso se pueden producir dentro de un mismo proceso o entre procesos distintos.  Un cambio de subproceso puede originarse porque un subproceso solicita información a otro o porque un subproceso de mayor prioridad que está listo para ejecutarse se adelanta a otro subproceso.|