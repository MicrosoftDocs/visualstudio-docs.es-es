---
title: Vista Interacciones de capas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 012d79a99ee8df2acf26106be922fac8c335fae3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878031"
---
# <a name="tier-interactions-view"></a>Interacciones de capas (Vista)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución de funciones de aplicaciones de varias capas que se comunican con las bases de datos a través de servicios de [!INCLUDE[vstecado](../includes/vstecado-md.md)]. Los datos se recopilan solamente para las llamadas a funciones sincrónicas.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]  
  
  La vista de interacciones muestra datos de interacción de capas en dos paneles:  
  
- El panel principal es un árbol jerárquico. La fila de nivel superior contiene los datos agregados para las conexiones de base de datos de un página de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] o un proceso. Los nodos secundarios contienen datos agregados para las conexiones de base de datos del elemento primario.  
  
- Al hacer clic en un nodo de llamada a la base de datos en el panel principal, los datos de la instancia de la llamada a la base de datos se muestran en el panel de detalles.  
  
  La hora se muestra como el número de milisegundos o el número de ciclos de reloj de la CPU. Para cambiar la unidad de tiempo que se muestra, haga clic en el menú **Herramientas**, haga clic en **Opciones** y después elija uno de las opciones de **Mostrar valores de tiempo como**.  
  
## <a name="master-pane"></a>Panel principal  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Name**|-   Para una fila de nivel superior, el nombre de la página web o del proceso del que se generaron perfiles.<br />-   Para una fila de conexión de base de datos, el nombre del servidor que hospeda la base de datos.|  
|**Base de datos**|El nombre de la base de datos (solo filas de conexión de base de datos).|  
|**Recuento**|El número total de solicitudes generadas por el proceso, la página web o la conexión de base de datos.|  
|**Tiempo total transcurrido**|El tiempo total dedicado a ejecutar cualquier solicitud del proceso, la página web o la conexión de base de datos.|  
|**Tiempo máximo transcurrido**|El tiempo máximo dedicado a ejecutar cualquier solicitud del proceso, la página web o la conexión de base de datos.|  
|**Tiempo mínimo transcurrido**|El tiempo mínimo dedicado a ejecutar cualquier solicitud del proceso, la página web o la conexión de base de datos.|  
|**Promedio de tiempo transcurrido**|El promedio de tiempo dedicado a ejecutar una solicitud del proceso, la página web o la conexión de base de datos.|  
  
## <a name="database-connection-details-pane"></a>Panel Detalles de conexión de la base de datos  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Texto de comando**|La consulta SQL de la solicitud.|  
|**Número de consultas**|El número de veces que se ejecutó la consulta.|  
|**Tiempo total transcurrido**|El tiempo total dedicado a ejecutar las instancias de la consulta.|  
|**Tiempo máximo transcurrido**|El tiempo máximo dedicado a ejecutar cualquier instancia de la consulta.|  
|**Tiempo mínimo transcurrido**|El tiempo mínimo dedicado a ejecutar cualquier instancia de la consulta.|  
|**Promedio de tiempo transcurrido**|El tiempo mínimo dedicado a ejecutar una instancia de la consulta.|



