---
title: Configuración de los parámetros de ejecución de pruebas de carga en Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: acd2ccd526e32670afa947148f25606aee1299be
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382427"
---
# <a name="configure-load-test-run-settings"></a>Configurar los parámetros de ejecución de pruebas de carga

Los *parámetros de ejecución* son un conjunto de propiedades que influyen en la manera en que se ejecuta una prueba de carga. Los parámetros de ejecución están organizados por categorías en la ventana **Propiedades**.

Puede tener más de un parámetro de ejecución en una prueba de carga, aunque solo uno de los parámetros de ejecución puede estar activo en cada ejecución. Los demás ofrecen una forma rápida de seleccionar parámetros alternativos para utilizar en posteriores ejecuciones de pruebas.

Los parámetros de ejecución iniciales se crean al generar una prueba de carga mediante el **Asistente para prueba de carga nueva**.

![Parámetros de ejecución de pruebas de carga](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-----------|-----------------------|
|**Agregar más parámetros de ejecución a la prueba de carga:** además del parámetro de ejecución que se crea al ejecutar el **Asistente para prueba de carga nueva**, puede agregar más parámetros de ejecución a la prueba de carga y hacer la prueba en condiciones diferentes.|-   [Cómo: Agregar más parámetros de ejecución a una prueba de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Especificar los parámetros de ejecución activa para utilizar con la prueba de carga:** puede seleccionar el parámetro de ejecución que desea utilizar con la prueba de carga utilizando el Editor de pruebas de carga. El sufijo "[Activo]" identifica los parámetros de ejecución activa".|-   [Cómo: Seleccionar el parámetro de ejecución activo para una prueba de carga](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Modificar las propiedades de los parámetros de ejecución:** puede modificar las propiedades para cuestiones como registrar opciones (vea más abajo), determinar la longitud de la prueba, la duración del precalentamiento, el número máximo de detalles de errores, la velocidad de muestreo, el modelo de conexión, el tipo de almacenamiento de resultados (solo pruebas de rendimiento web), el nivel de validación y el seguimiento de SQL. En los parámetros de ejecución deben reflejarse los objetivos de la prueba de carga.|-   [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md)<br />-   [Cambiar las propiedades de los parámetros de ejecución](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Especificar el número de iteraciones de pruebas en los parámetros de ejecución de pruebas de carga:** puede especificar el número de veces que se ejecutan todas las pruebas unitarias y de rendimiento web en todos los escenarios de prueba de carga configurando la propiedad **Iteraciones de prueba**.|-   [Cómo: Especificar el número de iteraciones de prueba del parámetro de ejecución](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Especificar la frecuencia de muestreo para un parámetro de ejecución de la prueba de carga:** puede especificar con qué frecuencia la prueba de carga recopila los datos del contador de rendimiento configurando la propiedad **Frecuencia de muestreo**.|-   [Cómo: Especificar la frecuencia de muestreo](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Especificar la opción de almacenamiento de detalles de tiempo:** puede especificar cómo desea que se guarden los detalles de la prueba de carga configurando la propiedad **Almacenamiento de detalles de tiempo**.|-   [Cómo: Especificar la propiedad Almacenamiento de detalles de tiempo](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Especificar el período de retención de recursos de prueba:** puede acelerar el ciclo de prueba > corrección > nueva prueba si conserva los recursos de la prueba durante un período concreto. Para ello, especifique la propiedad **Tiempo de retención de recursos**.|-   [Conservar los recursos necesarios para acelerar las pruebas de carga](/vsts/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Utilizar los parámetros de contexto:** puede utilizar los parámetros de contexto para parametrizar una cadena. Por ejemplo, si la prueba de carga contiene una prueba de rendimiento web que usa un servidor web parametrizado, puede agregar un parámetro de contexto a los parámetros de ejecución que se asigne a un servidor diferente.|-   [Cómo: Agregar parámetros de contexto a parámetros de ejecución](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Configurar las propiedades de registro de pruebas:** puede configurar con qué frecuencia se escriben los datos en el registro que está asociado con los parámetros de ejecución de pruebas de carga. Esto es importante cuando se ejecuta una prueba de carga grande o compleja porque el registro puede alcanzar varios gigabytes.<br /><br /> También puede configurar el archivo de registro para que se guarde automáticamente cuando la prueba de carga no pueda depurar y analizar la aplicación.|-   [Modificar la configuración de registro de pruebas de carga](../test/modify-load-test-logging-settings.md)|