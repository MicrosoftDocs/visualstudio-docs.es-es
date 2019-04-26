---
title: Escenarios de prueba de carga
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 647548a59c965b6feacb994efa041ecd5b6c6b91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786174"
---
# <a name="edit-load-test-scenarios"></a>Edición de escenarios de prueba de carga

Un *escenario* de prueba de carga especifica el modelo de carga, la combinación de pruebas, la combinación de exploradores y la combinación de redes. Los escenarios son importantes porque permiten configurar pruebas en las que se simulan cargas de trabajo realistas y complejas.

Por ejemplo, si va a probar un sitio de comercio electrónico que tiene un front-end de Internet que utilizarán cientos de clientes simultáneos, con velocidades de conexión muy diferentes y exploradores distintos. El mismo sitio también podría tener una función de administración utilizada por empleados internos para actualizar productos y para ver estadísticas. Estos usuarios internos normalmente tendrían acceso al sitio utilizando el mismo explorador y una conexión LAN de alta velocidad. Podría encapsular las propiedades de estos dos grupos de usuarios diferentes en escenarios diferentes. Cada escenario puede contener un tipo de usuario virtual. En este caso, se puede crear un escenario de prueba de carga que represente a clientes virtuales y otro escenario para representar a usuarios internos virtuales de un sitio web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Componentes del escenario

Las opciones y los valores de configuración iniciales que se especifican al crear una prueba de carga se pueden modificar más adelante en el **Editor de pruebas de carga**. También se pueden agregar nuevos escenarios, parámetros de ejecución y conjuntos de contadores a una prueba de carga.

![Escenarios de prueba de carga](../test/media/loadtesteditinscenarios.png)

Los escenarios contienen los componentes siguientes:

|Término|Definición|
|-|-|
|Combinación de exploradores|Simula que los usuarios virtuales acceden a un sitio web a través de diversos exploradores web.|
|Modelo de carga|Especifica el número de usuarios virtuales que están activos durante una prueba de carga y la tasa con que se inician nuevos usuarios. Por ejemplo: de pasos, constante y basada en objetivos.|
|Modelo de combinación de pruebas|Especifica la probabilidad de que un usuario virtual ejecute una prueba determinada en un escenario de prueba de carga. Por ejemplo: 20 % de posibilidades de ejecutar la PruebaA y 80 % de ejecutar la PruebaB. El modelo de combinación de pruebas debe reflejar los objetivos de la prueba para un escenario determinado.|
|Combinación de pruebas|La combinación de pruebas es la selección de pruebas unitarias y de rendimiento web que constituyen el escenario, así como la distribución de esas pruebas.|
|Combinación de redes|Simula que los usuarios virtuales acceden a un sitio web a mediante una serie de conexiones de red. La combinación de redes ofrece opciones que incluyen LAN, módem por cable y otras.|

Un escenario tiene algunas otras propiedades que se pueden modificar mediante el **Editor de pruebas de carga**. Para más información, consulte [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-|-----------------------|
|**Agregar pausas de interacción humana artificial en el escenario:** Los tiempos de reflexión de usuario se usan para simular el comportamiento humano que hace que las personas esperen entre interacciones con un sitio web. Los tiempos de reflexión de usuario aparecen entre solicitudes en una prueba de rendimiento web y entre iteraciones de prueba en un escenario de prueba de carga. El uso de tiempos de reflexión en una prueba de carga puede ser útil para crear simulaciones de carga más precisas.|-   [Modificar los tiempos de reflexión de usuario para simular los retrasos de la interacción humana en un sitio web](../test/edit-think-times-in-load-test-scenarios.md)|
|**Especificar el número de usuarios virtuales para el escenario:** puede configurar las propiedades del modelo de carga para especificar cómo se ajusta la carga de usuarios simulada durante una prueba de carga. Obtiene tres patrones de carga integrados: constante, de pasos y basado en objetivos. Elija el modelo de carga y ajuste las propiedades en los niveles adecuados para los objetivos de su prueba de carga.|-   [Editar los modelos de carga para modelar las actividades de usuarios virtuales](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Configurar la probabilidad de que un usuario virtual ejecute una prueba en el escenario:** puede usar la combinación de pruebas, que especifica la probabilidad de que un usuario virtual ejecute una prueba determinada un escenario de prueba de carga. Esto le permite simular una carga de forma más realista. En lugar de tener un único flujo de trabajo en sus aplicaciones, puede disponer de varios, lo que supone una aproximación más real a la forma en que los usuarios finales interactúan con las aplicaciones.|-   [Editar modelos de combinación de texto](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Agregar o quitar una prueba unitaria o de rendimiento web de un escenario de prueba de carga:** Puede agregar o quitar una prueba unitaria o de rendimiento web de una prueba de carga en un escenario. Una prueba de carga contiene uno o varios escenarios, cada uno de los cuales contiene una o varias pruebas de rendimiento web o unitarias.|-   [Editar el modelo de combinación de pruebas](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Configurar la combinación de redes deseada para el escenario:** la combinación de redes permite simular de forma más realista la carga de la red en un escenario de prueba de carga. La carga se genera utilizando una combinación heterogénea de tipos de red en lugar de un tipo de red único. Se crea una aproximación más real a la forma en que los usuarios finales interactúan con las aplicaciones. El modelo de combinación de redes debe reflejar los objetivos de ese escenario.|-   [Especificar los tipos de redes virtuales](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Seleccione la combinación de exploradores web adecuada para el escenario:** La combinación de exploradores permite simular de forma más realista la carga web en un escenario de prueba de carga. La carga se genera utilizando una combinación heterogénea de exploradores, en lugar de un solo explorador. Se crea una aproximación más parecida a los exploradores que se utilizarán con sus aplicaciones.|-   [Especificar los tipos de exploradores web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Configurar los parámetros de iteración de prueba para el escenario:** puede modificar un escenario de prueba de carga para configurar los parámetros de iteración de prueba mediante el Editor de prueba de carga y la ventana Propiedades. De manera predeterminada, un escenario se configura sin especificar un máximo de iteraciones de pruebas. De manera opcional, puede configurar el número máximo de iteraciones del escenario y el tiempo de pausa entre ellas.|-   [Configurar las iteraciones de prueba de escenarios](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Configurar los valores de retraso para el escenario:** Puede usar el **Editor de pruebas de carga** y la ventana **Propiedades** para especificar un retraso antes de iniciar un escenario en una prueba de carga. Un ejemplo en el que puede que desee utilizar la propiedad **Retrasar hora de inicio** es si necesita que un escenario empiece a generar elementos que utiliza otro escenario. Puede retrasar el escenario consumidor para permitir que el escenario productor rellene algunos datos.|-   [Configurar los retrasos de inicio del escenario](../test/configure-scenario-start-delays.md)|
|**Especificar los equipos remotos que se van a usar en un escenario de prueba de carga:** después de crear una prueba de carga, puede modificar las propiedades del escenario de prueba de carga para indicar los agentes de prueba que quiera incluir. Para obtener más información, vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).|-   [Cómo: Especificar los agentes de pruebas que se van a usar](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Vea también

- [Editar pruebas de carga](../test/edit-load-tests.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)