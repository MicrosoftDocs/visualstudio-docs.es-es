---
title: Visor de eventos | Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: e6dea07b1c0644dcb9fb165785a2ccdc28463e74
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85291016"
---
# <a name="events-viewer"></a>Visor de eventos

El visor de eventos genérico muestra la actividad de la aplicación a través de una lista de eventos, como la carga del módulo, el inicio del subproceso y la configuración del sistema. Esta vista ayuda a diagnosticar mejor el funcionamiento de la aplicación dentro del generador de perfiles de Visual Studio.

## <a name="setup"></a>Programa de instalación

1. Seleccione **Alt + F2** para abrir el generador de perfiles de rendimiento en Visual Studio.

1. Active la casilla **Visor de eventos**.

   ![Casilla Visor de eventos activada](../profiling/media/eventsviewerselected.png "Casilla Visor de eventos activada")

1. Seleccione el botón **Iniciar** para ejecutar la herramienta.

1. Una vez que se inicie la ejecución de la herramienta, repase el escenario del que se van a generar perfiles en su aplicación. A continuación, seleccione **Detener recopilación** o cierre la aplicación para ver los datos.

   ![Una ventana que muestra Detener recopilación](../profiling/media/stopcollectioneventsviewer.png "Una ventana que muestra Detener recopilación")

Para más información sobre cómo aumentar la eficacia de la herramienta, consulte el artículo [Optimización de la configuración del generador de perfiles](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Comprensión de los datos

![Un seguimiento del visor de eventos](../profiling/media/eventviewertrace.png "Un seguimiento del visor de eventos")

|Nombre de columna|Descripción|
|----------|---------------------|
|Nombre del proveedor|El origen del evento|
|Nombre de evento|El evento tal y como lo especifica su proveedor|
|Text|Descripciones del proveedor, el nombre del evento y el id. del evento|
|Marca de tiempo (ms)|Cuándo se realizó el evento|
|Guid del proveedor|El id. del proveedor de eventos|
|Id. de evento|El id. del evento|
|Identificador del proceso|El proceso a partir del cual se produjo el evento (si se conoce)|
|Nombre del proceso|El nombre del proceso si se está ejecutando activamente|
|Id. de subproceso|El identificador del subproceso a partir del cual se produjo el evento (si se conoce)|

Si se omite alguna columna de forma predeterminada, haga clic con el botón derecho en uno de los encabezados de columna existentes y seleccione la columna que quiere agregar.

![Incorporación de columnas en el visor de eventos](../profiling/media/eventvieweraddcolumns.png "Incorporación de columnas en el visor de eventos")

Al seleccionar un evento, aparece la ventana **Propiedades adicionales**. **Propiedades comunes** muestra la lista de propiedades que se mostrarán para cualquier evento. **Propiedades de carga** muestra propiedades específicas del evento. En el caso de algunos eventos, también puede ver las **Pilas**.

![El visor de eventos que muestra las pilas](../profiling/media/eventviewerstacks.png "El visor de eventos que muestra las pilas")

## <a name="organize-your-data"></a>Organización de los datos

Se pueden ordenar todas las columnas, excepto la columna **Texto**.

![El seguimiento del visor de eventos](../profiling/media/eventviewertrace.png "El seguimiento del visor de eventos")

El visor de eventos muestra hasta 20 000 eventos a la vez. Para centrarse en los eventos de interés, puede seleccionar el filtro de evento para filtrar la presentación de los eventos. También puede ver el porcentaje del número total de eventos que se han producido para cada proveedor. Mantenga el mouse sobre un solo filtro de evento para ver información rápida que muestra:

- Nombre del evento.
- Proveedor
- GUID
- Porcentaje de eventos totales
- Recuento de eventos

![El filtro de eventos del visor de eventos](../profiling/media/eventviewereventfilter.png "El filtro de eventos del visor de eventos")

El filtro del proveedor muestra el porcentaje del número total de eventos que se han producido para cada proveedor. Mantenga el mouse sobre un solo proveedor para ver una información rápida similar con el nombre del proveedor, el porcentaje de eventos totales y el recuento de eventos.

![El filtro de proveedor del visor de eventos](../profiling/media/eventviewerproviderfilter.png "El filtro de proveedor del visor de eventos")
