---
title: Propiedades de los escenarios de prueba de carga
description: Obtenga información sobre cómo cambiar la configuración de las propiedades de los escenarios de prueba de carga en Visual Studio para las distintas propiedades descritas en este artículo.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 263a3a1f928fe42d1f5b910f82d0d4a6ea24412e
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328813"
---
# <a name="load-test-scenario-properties"></a>Propiedades de los escenarios de pruebas de carga

Cambie la configuración de las propiedades de los escenarios de prueba de carga en Visual Studio para satisfacer los requisitos de las pruebas de carga. En este artículo se incluyen las diversas propiedades de escenarios de prueba de carga por categoría.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>General

|Propiedad|Definición|
|-|----------------|
|**Name**|Nombre del escenario.|

## <a name="mix"></a>Combinación

|Propiedad|Definición|
|-|----------------|
|**Combinación de exploradores**|Especifica la combinación de exploradores web para la prueba de carga. Puede especificar tipos de explorador web diferentes y su distribución de la carga.<br /><br />Haga clic en el botón de puntos suspensivos **(…)** para abrir el cuadro de diálogo **Editar combinación de exploradores** y use **Agregar** y **Quitar** para seleccionar los tipos de exploradores web de la prueba de carga.<br /><br />Para obtener más información, vea [Especificar tipos de exploradores web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Combinación de redes**|Especifica la combinación de redes para la prueba de carga. Puede especificar qué tipos de red incluir y su distribución de carga.<br /><br />Haga clic en el botón de puntos suspensivos **(…)** para abrir el cuadro de diálogo **Editar combinación de redes** y use **Agregar** y **Quitar** para seleccionar los tipos de redes de la prueba de carga.<br /><br />Para obtener más información, vea [Especificar tipos de redes virtuales en un escenario de prueba de carga](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Combinación de pruebas**|Especifica el rendimiento web y la combinación de pruebas unitarias para la prueba de carga. Puede especificar qué pruebas incluir y su distribución de la carga.<br /><br />Haga clic en el botón de puntos suspensivos **(…)** para abrir el cuadro de diálogo **Editar combinación de pruebas** y use **Agregar** y **Quitar** para seleccionar las pruebas de la prueba de carga.<br /><br />Para obtener más información, vea [Edición de la combinación de pruebas para especificar qué pruebas de rendimiento web, unitarias y automatizadas de IU incluir en un escenario de prueba de carga](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Tipo de combinación de pruebas**|Especifica el modelo de combinación de pruebas para la prueba de carga.<br /><br />Haga clic en el botón de puntos suspensivos **(…)** para abrir el cuadro de diálogo **Editar combinación de pruebas** y use la lista desplegable de **Modelo de combinación de pruebas** para seleccionar el modelo que se va a usar en la prueba de carga.<br /><br />Para obtener más información, vea [Editar modelos de combinación de pruebas](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Opciones

|Propiedad|Definición|
|-|----------------|
|**Agentes que se usarán**|Especifica los agentes que se quieren usar en el escenario si la prueba de carga se ejecuta de forma remota. Por ejemplo, puede especificar un conjunto específico de agentes para mantener la coherencia al analizar las tendencias de rendimiento. Además, los agentes pueden estar distribuidos geográficamente, de forma que haya una afinidad entre los scripts que ejecutan y dónde se encuentra el agente.<br /><br />Los agentes deben estar separados por comas, por ejemplo, "**Agent1, Agent2, Agent3**". Al dejar la propiedad en blanco se indica que el escenario debería utilizar todos los agentes disponibles.<br /><br />Para obtener más información, vea [Cómo: Especificar los agentes de pruebas que se van a usar](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Aplicar distribución a intervalo de velocidad**|Valor booleano que se usa para especificar si se quieren aplicar retrasos de distribución típicos en el modelo de combinación de pruebas de la velocidad del usuario. Esta propiedad solo se aplica si la propiedad **Tipo de combinación de pruebas** está establecida en **A partir de la velocidad del usuario**.<br /><br />Para obtener más información, vea [Cómo: Aplicar distribución a intervalo de velocidad en un modelo de combinación de pruebas basado en el ritmo del usuario](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**Conmutación de IP**|Valor booleano que se usa para especificar si se emplea la conmutación de IP.<br /><br />La conmutación de IP permite a un agente de prueba enviar solicitudes a un servidor mediante un intervalo de direcciones IP. De esta forma se simulan llamadas procedentes de diferentes equipos cliente. La conmutación de IP es importante para realizar pruebas en una granja de servidores web con carga equilibrada. La mayoría de los equilibradores de carga establecen una afinidad entre un cliente y un servidor web determinado mediante la dirección IP del cliente. Si aparentemente todas las solicitudes proceden del mismo cliente, el equilibrador de carga no equilibrará la carga. Para obtener un buen equilibrio de carga en la granja de servidores web es importante que las solicitudes procedan de un intervalo de direcciones IP.<br /><br />La conmutación de IP solo está disponible con el agente de prueba.|
|**Iteraciones de pruebas máximas**|Valor numérico que se utiliza para especificar el número máximo de pruebas para ejecutarse en el escenario. Un valor de 0 no especifica ningún máximo.<br /><br />Para obtener más información, vea [Configurar iteraciones de prueba en un escenario de prueba de carga](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Porcentaje de nuevos usuarios**|Valor numérico que especifica el porcentaje de nuevos usuarios o primeros visitantes en el escenario.<br /><br />Para obtener más información, vea [Cómo: Especificar el porcentaje de usuarios virtuales que usan datos de caché web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Perfil de reflexión de usuario**|Especifica si el escenario va a usar **Distribución normal** o si el perfil de reflexión está **Activado** o **Desactivado**.<br /><br />Para obtener más información, vea [Modificar los tiempos de reflexión para simular los retrasos de la interacción humana en un sitio web en escenarios de pruebas de carga](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Control de tiempo

|Propiedad|Definición|
|-|----------------|
|**Retrasar hora de inicio**|Un valor que indica cuántas horas, minutos y segundos se retrasa el inicio del escenario después de iniciar la prueba de carga. Si la propiedad **Deshabilitar durante el calentamiento** está establecida en **True**, la cantidad de tiempo de espera se aplica después del período de preparación.<br /><br />Para más información, consulte [Configurar el retraso de la hora de inicio del escenario](../test/configure-scenario-start-delays.md).|
|**Deshabilitar durante el calentamiento**|Valor booleano que se usa para especificar si el escenario se debe ejecutar o no durante el valor de tiempo de la propiedad **Deshabilitar durante el calentamiento** especificado en el parámetro de ejecución de la prueba de carga.<br /><br />Para obtener más información sobre las propiedades de los parámetros de ejecución de pruebas de carga, vea [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).<br /><br />Para más información, consulte [Configurar el retraso de la hora de inicio del escenario](../test/configure-scenario-start-delays.md).|
|**Tiempos de reflexión entre iteraciones de prueba**|Valor numérico que se utiliza para especificar el tiempo de espera en segundos entre iteraciones.<br /><br />Para obtener más información, vea [Modificar los tiempos de reflexión para simular los retrasos de la interacción humana en un sitio web en escenarios de pruebas de carga](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Vea también

- [Modificar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
