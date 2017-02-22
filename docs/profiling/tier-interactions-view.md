---
title: "Interacciones de capas (Vista) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.tierinteraction"
helpviewer_keywords: 
  - "Interacciones de capas (vista)"
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Interacciones de capas (Vista)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución en funciones de aplicaciones de varias capas que se comunican con bases de datos a través de [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)].  Los datos se recopilan solamente para las llamadas a funciones sincrónicas.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 La vista de interacciones muestra datos de interacción de capas en dos paneles:  
  
-   El panel principal es un árbol jerárquico.  La fila del nivel superior contiene los datos agregados para las conexiones de bases de datos de una página [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o un proceso.  Los nodos secundarios contienen datos agregados para las conexiones de base de datos del primario.  
  
-   Al hacer clic en un nodo de llamada de base de datos en el panel principal, los datos para la instancia de la llamada de la base de datos se muestran en el panel de detalles.  
  
 El tiempo se muestra como el número de milisegundos o el número de ciclos de reloj de la CPU.  Para cambiar la unidad de tiempo mostrada, haga clic en el menú **Herramientas**, haga clic en **Opciones** y, a continuación, elija una de las opciones **Mostrar valores de hora como**.  
  
## Panel principal  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|-   Para una fila del nivel superior, el nombre del proceso para el que se generan perfiles o página web.<br />-   En una fila de conexión a base de datos, el nombre del servidor que hospeda la base de datos.|  
|**Base de datos**|El nombre de la base de datos \(solamente las filas de conexión de base de datos\).|  
|**Total**|Número total de solicitudes generadas por el proceso, la página web o la conexión de base de datos.|  
|**Tiempo total transcurrido**|Tiempo total empleado en ejecutar cualquiera de las solicitudes desde el proceso, la página web o la conexión de base de datos.|  
|**Tiempo máximo transcurrido**|El tiempo máximo empleado en ejecutar cualquiera de las solicitudes desde el proceso, la página web o la conexión de base de datos.|  
|**Tiempo mínimo transcurrido**|El tiempo mínimo empleado en ejecutar cualquiera de las solicitudes desde el proceso, la página web o la conexión de base de datos.|  
|**Promedio de tiempo transcurrido**|El tiempo medio empleado en ejecutar una solicitud desde el proceso, la página web o la conexión de base de datos.|  
  
## Panel de detalles de la conexión de base de datos  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Texto del comando**|Consulta SQL de la solicitud.|  
|**Recuento de consultas**|Número de veces que se ejecutó la consulta.|  
|**Tiempo total transcurrido**|Tiempo total empleado en ejecutar las instancias de la consulta.|  
|**Tiempo máximo transcurrido**|El tiempo máximo empleado en ejecutar cualquiera de las instancias de la consulta.|  
|**Tiempo mínimo transcurrido**|El tiempo mínimo empleado en ejecutar cualquiera de las instancias de la consulta.|  
|**Promedio de tiempo transcurrido**|El tiempo medio empleado en ejecutar una instancia de la consulta.|