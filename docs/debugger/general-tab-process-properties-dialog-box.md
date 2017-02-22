---
title: "Pesta&#241;a General (Cuadro de di&#225;logo Propiedades del proceso) | Microsoft Docs"
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
  - "Propiedades de procesos para Windows NT"
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pesta&#241;a General (Cuadro de di&#225;logo Propiedades del proceso)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use la pestaña **General** para obtener más detalles de un proceso concreto.  Para mostrar el [cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md), cambie el foco a la ventana [Vista Procesos](../debugger/processes-view.md).  Seleccione el nodo de un proceso en el árbol y, a continuación, elija **Propiedades** en el menú **Ver**.  
  
 En la pestaña **General** está disponible la configuración siguiente:  
  
|Entry|Descripción|  
|-----------|-----------------|  
|**Nombre de módulo**|El nombre del módulo.|  
|**Id. de proceso**|El identificador único del proceso.  Los números de identificador de procesos se reutilizan, por lo que identifican un proceso solamente mientras dure dicho proceso.  El tipo de objeto Process se crea cuando se ejecuta un programa.  Todos los subprocesos de un proceso comparten el mismo espacio de direcciones y tienen acceso a los mismos datos.|  
|**Base de prioridad**|Prioridad base actual de este proceso.  Los subprocesos de un proceso pueden aumentar y disminuir su propia prioridad base con respecto a la prioridad base del proceso.|  
|**Subprocesos**|Número de subprocesos que están activos actualmente en este proceso.|  
|**Tiempo de CPU**|Tiempo de CPU total gastado en este proceso y sus subprocesos.  Es igual al tiempo de usuario más el tiempo con privilegios.|  
|**Tiempo de usuario**|Tiempo transcurrido acumulado durante el cual los subprocesos de este proceso han estado ejecutando código en modo usuario en los subprocesos activos.  Las aplicaciones se ejecutan en modo usuario, como sucede con subsistemas tales como el administrador de ventanas y el motor gráfico.|  
|**Tiempo con privil.**|Tiempo transcurrido total durante el cual este proceso se ha estado ejecutando en modo con privilegios en subprocesos activos.  La capa de servicio, las rutinas ejecutivas y el kernel se ejecutan en modo con privilegios.  Los controladores de dispositivo de la mayoría de los dispositivos, salvo los adaptadores gráficos e impresoras, también se ejecutan en modo con privilegios.  Una parte del trabajo que realiza Windows para una aplicación puede aparecer en otros procesos del subsistema además de como tiempo con privilegios.|  
|**Tiempo transcurrido**|Tiempo transcurrido total durante el cual este proceso se ha estado ejecutando.|