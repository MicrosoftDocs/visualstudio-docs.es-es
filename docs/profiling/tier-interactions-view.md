---
title: Vista Interacciones de capas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4636a391e2472dbff427956077719e75f34a81de
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31584976"
---
# <a name="tier-interactions-view"></a>Interacciones de capas (Vista)

La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución de funciones de aplicaciones de varias capas que se comunican con las bases de datos a través de servicios de [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]. Los datos se recopilan solamente para las llamadas a funciones sincrónicas.

**Requisitos**

- Visual Studio Enterprise

La vista de interacciones muestra datos de interacción de capas en dos paneles:

- El panel principal es un árbol jerárquico. La fila de nivel superior contiene los datos agregados para las conexiones de base de datos de un página de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o un proceso. Los nodos secundarios contienen datos agregados para las conexiones de base de datos del elemento primario.

- Al hacer clic en un nodo de llamada a la base de datos en el panel principal, los datos de la instancia de la llamada a la base de datos se muestran en el panel de detalles.

 La hora se muestra como el número de milisegundos o el número de ciclos de reloj de la CPU. Para cambiar la unidad de tiempo que se muestra, haga clic en el menú **Herramientas**, haga clic en **Opciones** y después elija uno de las opciones de **Mostrar valores de tiempo como**.

## <a name="master-pane"></a>Panel principal

|Columna|Description|
|------------|-----------------|
|**Name**|- Para una fila de nivel superior, el nombre de la página web o del proceso del que se generaron perfiles.<br />- Para una fila de conexión de base de datos, el nombre del servidor que hospeda la base de datos.|
|**Base de datos**|El nombre de la base de datos (solo filas de conexión de base de datos).|
|**Recuento**|El número total de solicitudes generadas por el proceso, la página web o la conexión de base de datos.|
|**Tiempo total transcurrido**|El tiempo total dedicado a ejecutar cualquier solicitud del proceso, la página web o la conexión de base de datos.|
|**Tiempo máximo transcurrido**|El tiempo máximo dedicado a ejecutar cualquier solicitud del proceso, la página web o la conexión de base de datos.|
|**Tiempo mínimo transcurrido**|El tiempo mínimo dedicado a ejecutar cualquier solicitud del proceso, la página web o la conexión de base de datos.|
|**Promedio de tiempo transcurrido**|El promedio de tiempo dedicado a ejecutar una solicitud del proceso, la página web o la conexión de base de datos.|

## <a name="database-connection-details-pane"></a>Panel Detalles de conexión de la base de datos

|Columna|Description|
|------------|-----------------|
|**Texto de comando**|La consulta SQL de la solicitud.|
|**Número de consultas**|El número de veces que se ejecutó la consulta.|
|**Tiempo total transcurrido**|El tiempo total dedicado a ejecutar las instancias de la consulta.|
|**Tiempo máximo transcurrido**|El tiempo máximo dedicado a ejecutar cualquier instancia de la consulta.|
|**Tiempo mínimo transcurrido**|El tiempo mínimo dedicado a ejecutar cualquier instancia de la consulta.|
|**Promedio de tiempo transcurrido**|El tiempo mínimo dedicado a ejecutar una instancia de la consulta.|