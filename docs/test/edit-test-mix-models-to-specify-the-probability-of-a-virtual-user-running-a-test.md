---
title: Edición de modelos de combinación de pruebas en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, virtual users
ms.assetid: e3b7d952-9012-400a-8131-3444390a6066
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 32fc3ef0684c89c422fac76550ba1fa123eb2f6b
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180446"
---
# <a name="edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test"></a>Edición de modelos de combinación de pruebas para especificar la probabilidad de que un usuario virtual ejecute una prueba

El *modelo de combinación de pruebas* especifica la probabilidad de que un usuario virtual ejecute una prueba determinada en un escenario de prueba de carga. Esto le permite simular una carga de forma más realista. En lugar de tener un único flujo de trabajo en sus aplicaciones, puede disponer de varios, lo que supone una aproximación más real a la forma en que los usuarios finales interactúan con las aplicaciones.

## <a name="test-mix-model-options"></a>Opciones del modelo de combinación de pruebas

Puede especificar una de las siguientes opciones de modelo de combinación de pruebas para el escenario de la prueba de carga:

-   **Basado en el número total de pruebas:** determina qué prueba unitaria o de rendimiento web se ejecuta cuando un usuario virtual inicia una iteración de prueba. Al final de la prueba de carga, el número de veces que se ha ejecutado una prueba determinada coincide con la distribución de pruebas asignada. Use este modelo de combinación de pruebas cuando base la combinación de pruebas en porcentajes de transacciones en un registro de IIS o en datos de producción.

-   **Basado en el número de usuarios virtuales:** determina el porcentaje de usuarios virtuales que ejecutan una prueba unitaria o de rendimiento web determinada. En cualquier punto de la prueba de carga, el número de usuarios que ejecutan una prueba determinada coincide con la distribución asignada. Use este modelo de combinación de pruebas cuando base la combinación de pruebas en el porcentaje de usuarios que ejecutan una prueba determinada.

-   **Basado en la velocidad del usuario:** durante la prueba de carga, cada prueba unitaria o de rendimiento web se ejecuta un número especificado de veces por usuario y por hora. Use este modelo de combinación de pruebas cuando desee que los usuarios virtuales ejecuten pruebas a una determinada velocidad durante la prueba de carga.

-   **Basado en el orden secuencial:** cada usuario virtual ejecuta las pruebas unitarias o de rendimiento web en el mismo orden en que se definen en el escenario. El usuario virtual seguirá recorriendo las pruebas en este orden hasta que se complete la prueba de carga.

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-----------|-----------------------|
|**Especificar la combinación de pruebas para la prueba de carga:** cuando cree una prueba de carga, especifique los parámetros en el **Asistente para prueba de carga nueva**. En el **Asistente para prueba de carga nueva**, elija las pruebas web y unitarias existentes que desee agregar al escenario inicial. Después de haber agregado las pruebas al escenario, especifique la combinación de pruebas para el escenario.<br /><br /> Puede usar opciones de modelos de carga para predecir de forma más precisa el uso real esperado del sitio web o la aplicación cuyas pruebas de carga está realizando. Esto es importante porque una prueba de carga que no se basa en un modelo de carga preciso puede generar resultados engañosos.|-   [Emular el uso real esperado de una aplicación o un sitio web](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md)|
|**Editar el modelo de combinación de pruebas:** puede cambiar un escenario de prueba de carga para usar uno de los modelos de combinación de pruebas con el **Editor de pruebas de carga**.||
|**Configurar el intervalo de velocidad para un modelo de combinación de pruebas a partir de la velocidad del usuario:** si el escenario de prueba de carga está configurado para usar el modelo de combinación de pruebas **A partir de la velocidad del usuario**, puede especificar cómo quiere configurar el intervalo de velocidad de la distribución.|-   [Cómo: Aplicar la distribución al retraso del ritmo cuando se usa un modelo de combinación de pruebas basado en el ritmo del usuario](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|

## <a name="change-the-test-mix-model-in-a-scenario"></a>Cambiar el modelo de combinación de pruebas en un escenario

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de los escenarios de modo que satisfagan las necesidades y los objetivos de la prueba.

> [!NOTE]
> Para obtener una lista completa de las propiedades de configuración de carga y sus descripciones, consulte [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

Con el **Editor de pruebas de carga**, puede cambiar el modelo de combinación de pruebas en un escenario de prueba de carga mediante la edición de la propiedad **Tipo de combinación de pruebas** en la ventana **Propiedades**.

### <a name="to-change-the-test-mix-model"></a>Para cambiar el modelo de combinación de pruebas

1.  Abra una prueba de carga.

     Aparece el **Editor de pruebas de carga**. Se mostrará el árbol de la prueba de carga.

2.  En la carpeta *Escenarios* del árbol de la prueba de carga, elija el nodo del escenario en el que quiere especificar el número máximo de iteraciones de prueba.

3.  En el menú **Ver**, seleccione la ventana **Propiedades**.

     Se muestran las categorías y propiedades del escenario.

4.  En la propiedad **Tipo de combinación de pruebas**, elija el botón de puntos suspensivos (**…**).

     Aparecerá el cuadro de diálogo **Editar combinación de pruebas**.

5.  Elija la lista desplegable de **Modelo de combinación de pruebas** y seleccione el modelo de combinación de pruebas que quiere usar para el escenario.

6.  (Opcional) Modifique la combinación de pruebas con los botones **Agregar**, **Quitar** y **Distribuir** y los controles deslizantes de distribución. Para más información, consulte [Editar la combinación de pruebas para especificar qué pruebas incluir en un escenario de prueba de carga](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

7.  (Opcional) Especifique una prueba de rendimiento web y unitaria para inicializar o finalizar con las casillas y la selección de las pruebas deseadas. Para más información, consulte [Emular el uso real esperado de una aplicación o un sitio web](../test/emulate-real-world-usage-of-a-web-site-in-a-load-test-using-test-mix-models.md).

8.  Elija **Aceptar**.

     La ventana **Propiedades** muestra el nuevo modelo de combinación de pruebas para la propiedad **Tipo de combinación de pruebas**.

9. Después de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. Luego, puede ejecutar la prueba de carga con el nuevo valor de **Tipo de combinación de pruebas**.

## <a name="see-also"></a>Vea también

- [Editar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)