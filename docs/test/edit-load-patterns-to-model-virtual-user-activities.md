---
title: Modelos de carga para pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a15f771d2afa2b5c8e02eed99b3168a537365a3f
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895306"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Editar los modelos de carga para modelar las actividades de usuarios virtuales

Las propiedades del modelo de carga especifican cómo se ajusta la carga simulada del usuario durante una prueba de carga. Visual Studio proporciona tres modelos de carga integrados: constante, de pasos y basado en objetivos. Elija el modelo de carga y ajuste las propiedades en los niveles adecuados para los objetivos de su prueba de carga.

El modelo de carga es un componente de un escenario. Los escenarios, junto con sus modelos de carga definidos, constituyen una prueba de carga.

> [!NOTE]
> En todos los modelos de carga, la carga que genera Visual Studio es una carga simulada de usuarios virtuales.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Modelos de carga

### <a name="constant"></a>Constante

 El modelo de carga constante se utiliza para especificar una carga de usuarios que no cambia durante la prueba de carga. Por ejemplo, cuando ejecuta una prueba de humo en una aplicación web, tal vez desee establecer una carga constante y ligera de 10 usuarios.

#### <a name="constant-load-pattern-considerations"></a>Consideraciones sobre el modelo de carga constante

 Los modelos de carga constante se usan para ejecutar la misma carga de usuario durante la ejecución de una prueba de carga. Tenga cuidado cuando use un modelo de carga constante con un recuento de usuarios elevado porque se puede hacer una demanda irrazonable y poco realista al servidor o servidores de prueba de carga. Por ejemplo, si la prueba de carga contiene una prueba web que comienza con la solicitud de una página principal y configura la prueba con una carga constante de 1000 usuarios, se enviarán las 1000 primeras solicitudes a la página principal lo más rápidamente posible. Esta puede no ser una simulación realista de acceso al sitio web. Para mitigarlo, considere el uso de un modelo de carga por pasos que aumenta gradualmente a 1000 usuarios o especifique un período de preparación en los parámetros de ejecución de la prueba de carga. Si se especifica un período de preparación, la prueba de carga aumentará gradualmente la carga durante dicho período de forma automática. Para más información, consulte [Configurar el retraso de la hora de inicio del escenario](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Paso

 El modelo de carga de pasos se utiliza para especificar una carga de usuarios que aumenta en el tiempo hasta una carga de usuarios máxima definida. Para incrementar las cargas paso a paso, especifique **Recuento inicial de usuarios**, **Recuento máximo de usuarios**, **Duración del paso (segundos)** y **Recuento de usuarios por pasos**.

 Por ejemplo, una carga por pasos con un **Recuento inicial de usuarios** de uno, un **Recuento máximo de usuarios** de 100, una **Duración del paso (segundos)** de 10 y un **Recuento de usuarios por pasos** de 1 crea un modelo de carga de usuarios que empieza en 1 y se incrementa en 1 cada 10 segundos hasta que se llega a 100 usuarios.

> [!NOTE]
> Si la duración total de la prueba es inferior al tiempo necesario para llegar paso a paso a la carga máxima de usuarios, la prueba se detiene cuando se agota la duración y no alcanza el objetivo de **Recuento máximo de usuarios**.


 Puede utilizar el objetivo por pasos para aumentar la carga hasta que el servidor llegue a un punto en que el rendimiento disminuye de manera considerable. A medida que aumente la carga, el servidor se quedará finalmente sin recursos. La carga por pasos resulta una buena forma de determinar el número de usuarios con el que esto ocurre. Con la carga por pasos, también tiene que supervisar atentamente los recursos de agente para asegurarse de que los agentes pueden generar la carga deseada.

 Por lo general, debe efectuar varias ejecuciones con pasos de distinta duración y diferentes recuentos de usuarios por paso para obtener buenas medidas para una carga determinada. Es frecuente que las cargas muestren un pico inicial en cada paso cuando se agrega a los usuarios. Mantener la carga en esa tasa le permite medir el rendimiento del sistema cuando éste se recupere del pico inicial.

#### <a name="step-load-pattern-considerations"></a>Consideraciones sobre el modelo de carga por pasos

 Se puede usar un modelo de carga de pasos para aumentar la carga en el servidor o los servidores mientras se ejecuta la prueba de carga, de forma que se vea cómo varía el rendimiento a medida que aumenta la carga de usuarios. Por ejemplo, para observar el rendimiento del servidor o servidores cuando aumenta la carga de usuarios a 2000, ejecute una prueba de carga de 10 horas utilizando un modelo de carga de pasos con las siguientes propiedades:

- **Recuento inicial de usuarios**: 100

- **Recuento máximo de usuarios**: 2000

- **Duración del paso (segundos)**: 1800

- **Tiempo de rampa de paso (segundos)**: 20

- **Recuento de pasos de usuario**: 100

  Estas configuraciones hacen que la prueba de carga se ejecute durante 30 minutos (1800 segundos) con cargas de 100, 200, 300 y hasta 2000 usuarios. La propiedad **Tiempo de rampa de paso** merece mención aparte, porque es la única de estas propiedades que no está disponible en el **Asistente para prueba de carga nueva**. Esta propiedad permite que el aumento de un paso al siguiente (por ejemplo, de 100 a 200 usuarios) se produzca de manera gradual, en lugar de inmediatamente. En el ejemplo, la carga de usuarios aumentaría de 100 a 200 usuarios en un período de 20 segundos (un aumento de cinco usuarios cada segundo). Para más información, consulte [Cómo: Especificar la propiedad Step Ramp Time para un modelo de carga por pasos](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Basado en objetivos

 Un modelo de carga basado en objetivos se parece al modelo de pasos, pero ajusta la carga de usuarios en función de umbrales del contador de rendimiento frente a ajustes periódicos de la carga de usuarios. Las cargas basadas en objetivos son útiles para una serie de propósitos diferentes:

- Maximizar el resultado de los agentes: mida la métrica limitadora de claves en el agente para maximizar el resultado de los agentes. Normalmente, es la CPU; sin embargo, también podría ser la memoria.

- Alcanzar cierto objetivo de nivel de recursos, normalmente la CPU, en el servidor de destino, y después medir el rendimiento en ese nivel. Esto le permite realizar comparaciones del rendimiento entre ejecuciones, dado un nivel coherente de uso de recursos en el servidor.

- Alcanzar un objetivo de nivel de rendimiento en el servidor.

  En la siguiente tabla, hay un ejemplo que muestra un modelo basado en objetivos con la siguiente configuración de propiedades:

|Grupo de propiedades|Propiedad.|Valor|
|-|--------------|-|
|Contador de rendimiento|Categoría|Procesador|
|Contador de rendimiento|Equipo|ContosoServer1|
|Contador de rendimiento|Contador|% de tiempo de procesador|
|Contador de rendimiento|Instancia|_Total|
|Intervalo de destino para el contador de rendimiento|Valor máximo|90|
|Intervalo de destino para el contador de rendimiento|Valor mínimo|70|
|Límites de recuento de usuarios|Recuento inicial de usuarios|1|
|Límites de recuento de usuarios|Recuento máximo de usuarios|100|
|Límites de recuento de usuarios|Disminución del recuento máximo de usuarios|5|
|Límites de recuento de usuarios|Incremento del recuento máximo de usuarios|5|
|Límites de recuento de usuarios|Recuento mínimo de usuarios|1|

 Esta configuración hace que el **Analizador de pruebas de carga** ajuste la carga de usuarios entre 1 y 100 durante una ejecución de prueba de tal forma que el **Contador** de `% Processor Time` de WebServer01 oscile entre `70%` y `90%.`.

 El tamaño de cada ajuste de la carga de usuarios se determina mediante los valores de **Incremento del recuento máximo de usuarios** y **Disminución del recuento máximo de usuarios**. Los límites de recuento de usuarios se establecen mediante las propiedades **Recuento máximo de usuarios** y **Recuento mínimo de usuarios**.

#### <a name="goal-based-load-pattern-considerations"></a>Consideraciones sobre el modelo de carga basado en objetivos

 Un modelo de carga basado en objetivos es útil cuando se desea determinar el número de usuarios que el sistema puede admitir antes de llegar a un nivel de utilización de servicios. Esta opción funciona mejor cuando ya se ha identificado el recurso que limita en el sistema (es decir, el cuello de botella).

 Por ejemplo, suponga que sabe que el recurso que límite el sistema es la CPU del servidor de bases de datos, y desea ver cuántos usuarios se admiten cuando la CPU está ocupada al 75% aproximadamente. Puede utilizar un modelo de carga basado en objetivos con el fin de mantener el valor "% tiempo de procesador" del contador de rendimiento entre el 70 y el 80 por ciento.

 Un aspecto que hay que controlar es si algún otro recurso está limitando el rendimiento del sistema. Dichos recursos pueden hacer que el objetivo especificado por el modelo de carga nunca se alcance. Asimismo, la carga de usuario sigue subiendo hasta alcanzar el valor especificado en **Recuento máximo de usuarios**. Esta no es normalmente la carga deseada, de modo que hay que tener cuidado sobre la opción del contador de rendimiento en el modelo de carga basado en objetivos.

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-|-----------------------|
|**Especificar el modelo de carga inicial de la prueba de carga:** al crear una prueba de carga mediante el **Asistente para prueba de carga nueva**, debe seleccionar un modelo de carga.|-   [Cambio del modelo de carga](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Editar el modelo de carga de la prueba de carga:** después de crear la prueba de carga, puede modificar el modelo de carga en el **Editor de pruebas de carga**.|-   [Cómo: Especificar la propiedad Step Ramp Time para un modelo de carga por pasos](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Especificar si los usuarios virtuales del escenario de prueba de carga deben incluir datos de memoria caché web:** puede cambiar la propiedad **Porcentaje de nuevos usuarios** para influir en la manera en la que la prueba de carga simula el almacenamiento en caché web realizado por un explorador web para los usuarios virtuales.|-   [Cómo: Especificar el porcentaje de usuarios virtuales que usan datos de caché web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Especificar el tiempo de rampa de paso para un modelo de carga de pasos:** la propiedad **Tiempo de rampa de paso** permite que el aumento de un paso al siguiente (por ejemplo, de 100 a 200 usuarios) se produzca de manera gradual en lugar de inmediatamente.|-   [Cómo: Especificar la propiedad Step Ramp Time para un modelo de carga por pasos](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Cambio del modelo de carga

 Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades del modelo de carga asociadas a un escenario a niveles en los que se cumplan los objetivos de la prueba.

> [!NOTE]
> Para obtener una lista completa de las propiedades de los escenarios de pruebas de carga y sus descripciones, consulte [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).


 Un modelo de carga especifica el número de usuarios virtuales activos durante una prueba de carga y la velocidad con que se agregan nuevos usuarios. Puede elegir entre las tres tramas disponibles: la de pasos, la constante y la basada en objetivos. Para más información, consulte [Specify the number of virtual users with load patterns in a load test scenario](../test/edit-load-patterns-to-model-virtual-user-activities.md) (Especificar el número de usuarios virtuales con modelos de carga en un escenario de prueba de carga).

> [!NOTE]
> También puede cambiar las propiedades de carga mediante programación usando un complemento de prueba de carga. Para más información, consulte [Cómo: Crear un complemento de pruebas de carga](../test/how-to-create-a-load-test-plug-in.md).


### <a name="to-change-the-load-pattern"></a>Para cambiar el modelo de carga

1.  Abra una prueba de carga.

2.  En el **Editor de pruebas de carga**, en la carpeta *Escenarios*, expanda el escenario cuyo modelo de carga quiere editar y elija el modelo de carga del escenario.

    > [!NOTE]
    > El texto del nodo Modelo de carga, tal y como se muestra en el árbol de escenarios de la prueba de carga, refleja el perfil de carga que eligió al crear la prueba de carga. Puede ser **Perfil de carga constante** o **Perfil de carga por pasos**.

3.  Presione **F4** para abrir la ventana **Propiedades**.

     Las categorías **Modelo de carga** y **Parámetros** se muestran en la ventana **Propiedades**.

4.  (Opcional) Cambie la propiedad **Modelo** en la categoría **Modelo de carga**.

     Las opciones para la propiedad **Modelo** son **Paso**, **Constante** y **Basado en objetivos**. Para más información sobre los tipos de modelos de carga, consulte [Specifying the Number of Virtual Users with Load Patterns in a Load Test Scenario](../test/edit-load-patterns-to-model-virtual-user-activities.md) (Especificar el número de usuarios virtuales con modelos de carga en un escenario de prueba de carga).

5.  (Opcional) En la categoría **Parámetros**, cambie los valores.

    > [!NOTE]
    > Los valores que puede establecer para **Parámetros** difieren según el valor que se haya seleccionado para la propiedad **Modelo**.

6.  Cuando haya terminado de cambiar las propiedades, elija **Guardar** en el menú **Archivo**. Entonces podrá ejecutar la prueba de carga con el nuevo modelo de carga.

## <a name="see-also"></a>Vea también

- [Modificar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Cómo: Especificar el porcentaje de usuarios virtuales que usan datos de caché web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Cómo: Especificar la propiedad Step Ramp Time para un modelo de carga por pasos](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)