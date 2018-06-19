---
title: Creación y ejecución de una prueba de carga en Visual Studio
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 22014010ea0ef7d101a446b6e89591797f5f2550
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977390"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Tutorial: Crear y ejecutar una prueba de carga que contiene pruebas unitarias

En este tutorial se crea una prueba de carga que contiene pruebas unitarias.

Este tutorial le guiará por el proceso de creación y posterior ejecución de una prueba de carga mediante Visual Studio Enterprise. Una prueba de carga es un contenedor de pruebas de rendimiento web y pruebas unitarias. Las pruebas de carga se crean con el Asistente para prueba de carga nueva.

Una prueba de carga también expone muchas propiedades en tiempo de ejecución, que se pueden modificar para generar la simulación de carga deseada. En este tutorial, usará el Asistente para prueba de carga nueva con el fin de agregar pruebas unitarias a una prueba de carga.

En este tutorial, se realizarán las siguientes tareas:

-   Crear una prueba de carga que utiliza pruebas unitarias.

-   Cambiar algunas opciones de configuración de la prueba de carga.

-   Ejecutar una prueba de carga.

-   Siga los pasos de [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) para crear una sencilla biblioteca de clases de C# que contenga un proyecto de prueba de carga y rendimiento web con algunas pruebas unitarias.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Crear una prueba de carga que contenga pruebas unitarias mediante el Asistente para prueba de carga nueva

### <a name="to-start-the-new-load-test-wizard"></a>Para iniciar el Asistente para prueba de carga nueva

1.  Abra la solución Bank creada en [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

2.  En el **Explorador de soluciones**, abra el menú contextual del nodo de la solución Bank, elija **Agregar** y, luego, **Nuevo proyecto**.

     Aparece el cuadro de diálogo Agregar nuevo proyecto.

3.  En el cuadro de diálogo Agregar nuevo proyecto, expanda **Visual C#** y elija **Prueba**. En la lista de plantillas, elija **Proyecto de prueba de carga y rendimiento web** y, en el campo **Nombre**, escriba `BankLoadTest`. Elija **Aceptar**.

     El proyecto de prueba de carga y rendimiento web BankLoadTest se agrega a la solución.

4.  Abra el menú contextual del nuevo proyecto de prueba de carga y rendimiento web BankLoadTest, elija **Agregar** y, luego, **Prueba de carga**.

5.  Se inicia el **Asistente para prueba de carga nueva**.

6.  La primera página es la **Pantalla de bienvenida** del **Asistente para prueba de carga nueva**.

7.  Seleccione **Siguiente**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Para editar la configuración del escenario de prueba de carga

1.  En el cuadro de texto **Escribir un nombre para el escenario de prueba de carga**, escriba **ScenarioSample**.

     Un *escenario* es un mecanismo de agrupación. Está compuesto por un conjunto de pruebas y las propiedades para ejecutarlas bajo carga.

2.  Establezca **Perfil de tiempo de reflexión** en `Use normal distribution centered on recorded think times`. Los tiempos de reflexión representan el tiempo que un usuario reflexionaría sobre una página Web antes de pasar a la página siguiente.

1.  Cuando termine, elija **Siguiente**.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Para editar la configuración del modelo de carga para el escenario de prueba

1.  Elija **Carga por pasos**.

    > [!NOTE]
    > Puede elegir entre dos tipos de modelos de carga: constante y de pasos. Cada tipo cumple su función en las pruebas de carga, pero para los fines de este tutorial, elija **Carga por pasos**.

2.  Establezca **Iniciar recuento de usuarios** en 10 usuarios.

3.  Establezca **Duración del paso** en 10 segundos.

4.  Establezca **Recuento de usuarios por pasos** en 10 usuarios/paso.

5.  Establezca **Recuento máximo de usuarios** en 100 usuarios.

6.  Seleccione **Siguiente**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Para seleccionar el modelo de combinación de pruebas para el escenario

1.  En ¿Cómo debe modelarse la combinación de pruebas?, seleccione **A partir del número total de pruebas**.

2.  Seleccione **Siguiente**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Para agregar pruebas unitarias al escenario

1.  El paso siguiente es **Agregar pruebas a un escenario de prueba de carga y editar la combinación de pruebas**.

2.  Elija **Agregar** para seleccionar las pruebas.

3.  Elija las pruebas unitarias de CreditTest que aparecen en el panel **Pruebas disponibles**, donde se muestran todas las pruebas de rendimiento web y las pruebas unitarias del proyecto de prueba de carga y rendimiento web.

4.  Elija la flecha para agregar la prueba unitaria CreditTest al panel **Pruebas seleccionadas**.

5.  Repita los pasos 3 y 4 para las pruebas unitarias DebitTest y FreezeAccountTest.

6.  Cuando termine de agregar las tres pruebas unitarias, elija **Aceptar**.

     Se le muestra la combinación de pruebas.

7.  Mueva el control deslizante bajo Distribución para CreditTest ligeramente hacia la derecha para ajustar la distribución de las pruebas. Observe que los otros controles deslizantes se mueven automáticamente a la izquierda para que la distribución permanezca al 100%.

8.  Seleccione **Siguiente**.

### <a name="to-select-network-mix-for-test-scenario"></a>Para seleccionar la combinación de redes para el escenario de prueba

1.  Seleccione el tipo de conexión LAN para agregar a la combinación de anchos de banda de red.

     Puede agregar otros tipos de red adicionales. Utilice los controles deslizantes para ajustar la distribución y el peso de la prueba.

2.  Seleccione **Siguiente**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Para especificar los equipos que se van a supervisar con conjuntos de contadores durante la ejecución de pruebas de carga

1.  Seleccione **Siguiente**.

     Para obtener más información sobre los conjuntos de contadores, vea [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Para editar el parámetro de ejecución para la prueba de carga

1.  Seleccione **Duración de la prueba de carga** y, luego, establezca **Duración de la ejecución** en 2 minutos para la *prueba de comprobación de la compilación* de la prueba de carga.

     Cuando se compilan las pruebas de carga, lo más recomendable es validar que todo se ha configurado correctamente y se ejecuta según lo esperado, por medio de una prueba de carga ligera y breve. Este proceso se conoce como *prueba de comprobación de la compilación*.

2.  Elija **Finalizar**. La prueba de carga se abre en el **Editor de pruebas de carga**.

## <a name="running-the-load-test"></a>Ejecutar la prueba de carga
 Después de crear la prueba de carga, ejecútela para ver cómo responde la aplicación Bank a la simulación de carga. Mientras se ejecuta una prueba de carga, aparece la ventana **Analizador de pruebas de carga**.

### <a name="to-run-the-load-test"></a>Para ejecutar la prueba de carga

1.  Con una prueba de carga abierta en el **Editor de pruebas de carga**, elija el botón verde **Ejecutar prueba** de la barra de herramientas. Se inicia la ejecución de la prueba de carga.

2.  Si su simulación de prueba supera cualquier umbral, aparecerán iconos en los nodos de control de árbol para indicar una infracción del umbral. Los errores tienen un círculo rojo superpuesto; las advertencias tienen superpuesto un triángulo amarillo. Busque un contador que superara el umbral y, para representarlo gráficamente, arrastre su icono al gráfico. Puede hacerlo mientras se ejecuta la prueba.

## <a name="see-also"></a>Vea también

- [Modificar la combinación de las pruebas para especificar qué rendimiento web, pruebas unitarias y pruebas de IU codificada incluir en un escenario de prueba de carga](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Especificar tipos de redes virtuales](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Edición de escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Modificar modelos de carga para modelar las actividades de usuarios virtuales](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Modificar los modelos de combinación de texto para especificar la probabilidad de que un usuario virtual ejecute una prueba](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)