---
title: Conjuntos de contadores y reglas de umbral para pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 493295bdbcd1b4906aedf6dca54e264e8ae5e8c6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659961"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Especificar conjuntos de contadores y reglas de umbral para equipos en una prueba de carga

Las pruebas de carga proporcionan conjuntos de contadores con nombre que son útiles cuando se analizan datos de contadores de rendimiento. Los conjuntos de contadores están organizados por tecnología e incluyen Aplicación, ASP.NET, Aplicación .NET, IIS y SQL. Cuando se crea una prueba de carga con el **Asistente para prueba de carga nueva**, se agrega un conjunto inicial de contadores. Estos ofrecen una serie de conjuntos de contadores predefinidos e importantes para la prueba de carga. Los contadores se administran en el **Editor de pruebas de carga**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Si las pruebas de carga se distribuyen entre varios equipos remotos, los contadores de controlador y de agente se asignan automáticamente a los conjuntos de contadores de controlador y de agente. Para obtener más información sobre cómo usar máquinas remotas en la prueba de carga, vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).

Los conjuntos de contadores se recopilan en los equipos que especifique. La asociación entre un conjunto de contadores y un equipo que se usa durante una prueba de carga es una *asignación de conjunto de contadores*. Por ejemplo, el servidor web que se está probando podría tener asignaciones de conjuntos de contadores en aplicaciones de ASP.NET, IIS y .NET.

De forma predeterminada, los contadores de rendimiento se recopilan en el controlador y los agentes. Para obtener más información, vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).

Es importante que agregue los servidores sometidos a prueba a la lista de equipos en los que se van a recopilar contadores. Entonces, todos los datos del sistema importantes se recopilan y se supervisan durante la prueba de carga.

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-|-----------------------|
|**Administración de conjuntos de contadores de la prueba de carga:** después de crear la prueba de carga, puede editar el conjunto de contadores en el Editor de pruebas de carga. La administración de conjuntos de contadores implica la elección del conjunto de equipos del que desea recopilar datos de rendimiento, así como la asignación de un grupo de conjuntos de contadores para recopilar datos de cada equipo individual. Los contadores se administran en el Editor de prueba de carga.|-   [Cómo: Administrar conjuntos de contadores](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Agregar conjuntos de contadores a la prueba de carga:** Cuando se crea una prueba de carga con el **Asistente para prueba de carga nueva**, se agrega un conjunto de contadores inicial. Este conjunto inicial de contadores ofrece una serie de conjuntos de contadores predefinidos para la prueba de carga. Después de crear una prueba de carga, puede agregar nuevos contadores a los conjuntos de contadores existentes mediante el Editor de prueba de carga.|-   [Cómo: Agregar contadores a conjuntos de contadores](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Cómo: Agregar conjuntos de contadores personalizados](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Especificar una regla de umbral mediante contadores para la prueba de carga:** Una regla de umbral es una regla que se establece en un contador de rendimiento individual para supervisar el uso de los recursos del sistema durante una prueba de carga. Las definiciones de conjuntos de contadores contienen reglas de umbral predefinidas para muchos contadores de rendimiento clave. Las reglas de umbral de las pruebas de carga comparan un valor de contador de rendimiento con un valor constante o con otro valor de contador de rendimiento.|-   [Cómo: Agregar una regla de umbral](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Asignar nombres descriptivos a los equipos a los que están asignados los conjuntos de contadores:** puede agregar etiquetas de equipo que permitan aplicar un nombre fácilmente reconocible a un equipo. Las etiquetas se muestran en el nodo **Asignaciones de conjuntos de contadores** del árbol en el Editor de pruebas de carga. Lo que es más importante, las etiquetas se muestran en informes de Excel que ayudan a las partes interesadas a identificar qué rol desempeña el equipo en la prueba de carga, por ejemplo "Servidor web1 en laboratorio2" o "SQL Server2 en la oficina de Phoenix".<br /><br /> Para obtener más información, vea [Informar de los resultados de las pruebas de carga para las comparaciones de pruebas o los análisis de tendencias](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Usar conjuntos de contadores

Las herramientas de prueba de carga recopilan y plasman en gráficos los datos de rendimiento mediante el uso de contadores a lo largo del tiempo. Los datos de los contadores se recopilan a intervalos especificados por el usuario durante la ejecución de una prueba de carga. Para obtener más información, vea [Cómo: Especificar la frecuencia de muestreo](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Puede ver los contadores en tiempo de ejecución o después de la ejecución de una prueba de carga mediante el *Analizador de pruebas de carga*.

Los datos de los contadores se recopilan en el servidor y en cualquier equipo en el que se ejecute una prueba. Si ha configurado un conjunto de equipos agente en los que ejecutar pruebas, los contadores también se recopilan en esos equipos.

Hay tres categorías de contador: de porcentajes, de recuentos y de promedios. Algunos ejemplos son el porcentaje de uso de la CPU, los recuentos de bloqueo de SQL Server y las solicitudes de IIS por segundo.

![Conjuntos de contadores de la prueba de carga](../test/media/loadtestcountersets.png)

El equipo que ejecuta una prueba crea un informe con los datos de rendimiento de las solicitudes HTTP individuales. Por ejemplo, puede ser un equipo agente. Para las solicitudes, se podrían supervisar datos como el tiempo medio al primer byte, el tiempo de respuesta y las solicitudes por segundo.

Para facilitar la recolección de datos de rendimiento en un servidor web, Visual Studio Enterprise también proporciona conjuntos de contadores con nombre predefinidos, que se basan en la tecnología para uso en pruebas de carga. Estos conjuntos son útiles cuando se está analizando un servidor en el que se ejecuta IIS, ASP.NET o SQL Server. Los contadores no proporcionados en el conjunto predeterminado se pueden agregar utilizando el Editor de prueba de carga. Es importante agregar a la prueba de carga los equipos o servidores sometidos a prueba, para asegurarse de que es posible supervisar la utilización de recursos en estos equipos. Para obtener más información, vea [Cómo: Administrar conjuntos de contadores](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

El análisis de resultados de las ejecuciones de pruebas de carga normalmente requiere el conocimiento de un área determinada específico del dominio, para saber qué datos hay que recopilar, dónde conviene establecer reglas de umbral y cómo saber si una medida refleja un problema concreto en la aplicación. Para obtener más información, vea [Reglas de umbral](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Consideraciones sobre el intervalo de muestreo de los contadores de rendimiento

Seleccione un valor apropiado para la propiedad **Frecuencia de muestreo** en los parámetros de ejecución de pruebas de carga según la duración de la prueba de carga. Una velocidad de muestra menor, como el valor predeterminado de cinco segundos, necesita más espacio en la base de datos de resultados de pruebas de carga. En el caso de pruebas de carga más largas, el incremento de la velocidad de muestra reduce la cantidad de datos recopilados. Para obtener más información, vea [Cómo: Especificar la frecuencia de muestreo](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

A continuación se ofrecen algunas instrucciones para las velocidades de muestra.

|Duración de la prueba de carga|Velocidad de muestra recomendada|
|-|-----------------------------|
|\< 1 hora|5 segundos|
|De 1 a 8 horas|15 segundos|
|De 8 a 24 horas|30 segundos|
|> 24 horas|60 segundos|

## <a name="store-performance-data"></a>Almacenar datos de rendimiento

Durante la ejecución de una prueba de carga, se recopilan los datos del contador de rendimiento y se almacenan en el *repositorio de resultados de pruebas de carga*. Para más información, consulte [Administrar resultados de pruebas de carga en el repositorio de resultados de pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>Reglas de umbral

Una *regla de umbral* es una regla que se establece en un contador de rendimiento individual para supervisar el uso de recursos del sistema durante una prueba de carga. Las definiciones de conjuntos de contadores contienen reglas de umbral predefinidas para muchos contadores de rendimiento clave. Para obtener más información, vea [Using Counter Sets to Help Analyze Performance Counter Data in Load Tests](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md) (Usar conjuntos de contadores para ayudar a analizar datos de contadores de rendimiento en pruebas de carga).

## <a name="threshold-rules-and-levels"></a>Reglas y niveles de umbral

Al crear reglas de umbral en las pruebas de carga, hay que elegir entre dos tipos de reglas:

Comparar constante: compara un valor de contador de rendimiento con un valor constante.

Comparar contadores: compara un valor de contador de rendimiento con otro valor de contador de rendimiento.

Al crear reglas de umbral, hay que establecer también los niveles de la regla. Los niveles que puede definir son el umbral de advertencia y el umbral crítico. Al ver la ejecución de una prueba de carga, un símbolo amarillo indica las infracciones de umbral de nivel de advertencia y un símbolo rojo indica las infracciones de umbral de nivel crítico.

## <a name="the-alert-if-over-property"></a>Propiedad Alertar si se supera

Establezca la propiedad **Alertar si se supera** en **True** para indicar que exceder un umbral supone un problema. Por ejemplo, si la regla de umbral se establece en **% de tiempo de procesador** y quiere que se le avise si el valor es mayor que 90, use el tipo de regla **Comparar constante**, establezca el **Valor de umbral crítico** en 90 y establezca **Alertar si se supera** en **True**.

Establezca la propiedad **Alertar si se supera** en **False** para indicar que no alcanzar un umbral supone un problema. Por ejemplo, si la regla de umbral se establece en **Solicitudes por segundo** y quiere que se le avise si el valor es inferior a 50, use el tipo de regla **Comparar constante**, establezca el **Valor de umbral crítico** en 50 y establezca **Alertar si se supera** en **False**.

## <a name="see-also"></a>Vea también

- [Cómo: Agregar una regla de umbral](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analizar las infracciones de las reglas de umbral](../test/analyze-threshold-rule-violations-in-load-tests.md)