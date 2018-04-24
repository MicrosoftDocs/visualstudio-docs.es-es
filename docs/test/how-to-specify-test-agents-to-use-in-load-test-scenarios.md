---
title: Especificar los agentes de pruebas que se usarán en escenarios de prueba de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- test agents, load tests
- load tests, scenarios
- load tests, specifying for load tests
- tests agents, load tests, specifying
- load tests, test agents
ms.assetid: e86806dd-5897-4e4c-bfd4-8d687fb72a6e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: dd6ca0c9b92f8eaa27c2a8726cc9d2cea49636b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-test-agents-to-use-in-load-test-scenarios"></a>Cómo: Especificar los agentes de prueba que se usarán en escenarios de prueba de carga

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de los escenarios de modo que satisfagan las necesidades y los objetivos de la prueba.

> [!NOTE]
> Para obtener una lista completa de las propiedades de los escenarios de pruebas de carga y sus descripciones, vea [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

Los agentes se especifican con el Editor de pruebas de carga para cambiar la propiedad **Agentes que se usarán** en la ventana Propiedades.

Puede especificar los agentes que desea que se usen en el escenario si utiliza controladores y agentes para ejecutar la prueba de carga de forma remota. Por ejemplo, puede especificar un conjunto específico de agentes para mantener la coherencia al analizar las tendencias de rendimiento. Además, los agentes pueden estar distribuidos geográficamente, de forma que exista una afinidad entre los scripts que ejecutan y dónde se encuentra el agente.

> [!TIP]
> En lugar de colocar un agente en el sitio remoto físicamente, otra opción es utilizar la emulación de red para emular la red lenta. Para obtener más información, vea [Especificar los tipos de red virtual](../test/specify-virtual-network-types-in-a-load-test-scenario.md) en un [escenario de prueba de carga](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

Para obtener más información, vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).

Otra razón es que algunos, pero no todos, los agentes podrían tener software instalado en ellos que se precise para un escenario determinado.

Puede controlar la selección del agente para una ejecución de pruebas determinada utilizando roles en la configuración de pruebas. Para obtener más información, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

Si una máquina de agente de prueba utiliza más del 75 por ciento de la CPU o tiene menos del 10 por ciento de memoria física disponible, agregue más agentes a la prueba de carga para asegurarse de que la máquina del agente no se convierta en el cuello de botella de la prueba de carga.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Para especificar los agentes que se van a usar en un escenario

1.  Abra una prueba de carga.

     Aparecerá el Editor de prueba de carga. Se mostrará el árbol de la prueba de carga.

2.  En la carpeta **Escenarios** de los árboles de prueba de carga, elija el nodo del escenario en el que quiere especificar los agentes que se van a usar.

3.  En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades del escenario se muestran en la ventana Propiedades.

4.  En el cuadro de texto de la propiedad **Agentes que se usarán**, escriba la lista de agentes en los que se puede ejecutar el escenario.

     Los agentes deben estar separados por comas, por ejemplo, "**Agent1, Agent2, Agent3**". Al dejar la propiedad en blanco se indica que el escenario debería utilizar todos los agentes disponibles.

    > [!NOTE]
    > La propiedad **Agentes que se usarán** se omite en las ejecuciones locales. En las ejecuciones remotas, si no existe ninguno de los agentes especificados en **Agentes que se usarán**, no se ejecutan las pruebas en el escenario.

5.  Después de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. Luego, puede ejecutar la prueba de carga con el nuevo valor de **Agentes que se usarán**.

## <a name="see-also"></a>Vea también

- [Edición de escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Tutorial: Crear y ejecutar una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md)
- [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)