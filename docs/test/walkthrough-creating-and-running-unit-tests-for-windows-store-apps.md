---
title: Creación y ejecución de pruebas unitarias en aplicaciones para UWP
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: a123657e148e4c19c0fab1c1a9bf567ad2ea6fa8
ms.sourcegitcommit: 9a3972eb85de5443ac2bc03964c5a251c39b2921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/26/2019
ms.locfileid: "71301711"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Tutorial: Crear y ejecutar pruebas unitarias para aplicaciones UWP

Visual Studio incluye permite realizar pruebas unitarias de aplicaciones de la Plataforma universal de Windows (UWP). Visual Studio proporciona plantillas de proyecto de prueba unitaria para C#, Visual Basic y C++.

> [!TIP]
> Para obtener más información sobre cómo desarrollar aplicaciones UWP, consulte [Introducción a las aplicaciones para UWP](/windows/uwp/get-started/).

En los procedimientos siguientes se describen los pasos para crear, ejecutar y depurar pruebas unitarias para las aplicaciones de UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Crear un proyecto de prueba unitaria para una aplicación de UWP

::: moniker range=">=vs-2019"

1. Abra Visual Studio. En la ventana de inicio, elija **Crear un proyecto nuevo**.

2. En el cuadro de búsqueda de la página **Crear un nuevo proyecto**, escriba **prueba unitaria**.

   La lista de plantillas se filtra por las de las pruebas unitarias.

3. Seleccione la plantilla **Unit Test App (Universal Windows)** para C# o Visual Basic y, luego, seleccione **Siguiente**.

   ![Creación de una aplicación de prueba unitaria de UWP en Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Opcionalmente, cambie el nombre del proyecto o la solución y la ubicación y, luego, seleccione **Crear**.

5. Opcionalmente, cambie las versiones de plataforma mínima y de destino y, luego, seleccione **Aceptar**.

Después de realizar estos pasos, se crea el proyecto de prueba unitaria y se muestra en el Explorador de soluciones.

![Proyecto de prueba unitaria de UWP en el Explorador de soluciones](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. En el menú **Archivo** , elija **Nuevo proyecto**.

   Se muestra el cuadro de diálogo **Nuevo proyecto**.

2. En Plantillas, elija el lenguaje de programación en el que desea crear las pruebas unitarias y, a continuación, elija la biblioteca de pruebas unitarias de Windows Universal asociada. Por ejemplo, elija **Visual C#** y, luego, **Windows Universal**. Por último, elija **Unit Test Library (Universal Windows)** (Biblioteca de pruebas unitarias [Windows Universal]).

3. (Opcional) En el cuadro de texto **Nombre**, escriba el nombre que quiera usar para el proyecto.

4. (Opcional) Para modificar la ruta de acceso en la que quiera crear el proyecto, escríbala en el cuadro de texto **Ubicación** o elija el botón **Examinar** .

5. (Opcional) En el cuadro de texto nombre de **Solución** , escriba el nombre que desee usar para la solución.

6. Deje seleccionada la opción **Crear directorio para la solución** y elija el botón **Aceptar** .

   ![Biblioteca de pruebas unitarias adaptada](../test/media/unit_test_win8_1.png)

   El **Explorador de soluciones** se rellena con el nuevo proyecto de prueba unitaria de UWP y el editor de código muestra la prueba unitaria predeterminada denominada UnitTest1.

   ![Nuevo proyecto de prueba unitaria adaptada](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Editar el archivo de manifiesto de la aplicación para UWP del proyecto de prueba unitaria

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo *Package.appxmanifest* y elija **Abrir**.

2. En el **diseñador de manifiestos**, haga clic en la pestaña **Capacidades**.

3. En la lista, en **Capacidades**, seleccione las capacidades que necesita la prueba unitaria y el código para las pruebas. Por ejemplo, active la casilla **Internet** si la prueba unitaria lo necesita y el código que está probando necesita tener la capacidad de tener acceso a Internet.

   > [!NOTE]
   > Las capacidades que seleccione deben incluir solo las capacidades necesarias para que la prueba unitaria funcione correctamente.

   ![Manifiesto de pruebas unitarias](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Codificar la prueba unitaria para una aplicación de UWP

En el Editor de código, edite la prueba unitaria y agregue las aserciones y la lógica requeridas para las pruebas.

## <a name="run-unit-tests"></a>Ejecutar pruebas unitarias

Para compilar la solución y ejecutar la prueba unitaria mediante el Explorador de pruebas, siga estos pasos:

1. En el menú **Prueba** , seleccione **Windows**y, a continuación, elija **Explorador de pruebas**.

2. En el menú **Compilar** , elija **Compilar solución**.

   La prueba unitaria se muestra ahora en el Explorador de pruebas.

   > [!NOTE]
   > Debe compilar la solución para actualizar la lista de pruebas unitarias en el Explorador de pruebas.

3. En el **Explorador de pruebas**, elija la prueba unitaria que creó.

4. Elija **Ejecutar todas**.

   ![Explorador de pruebas unitarias; ejecutar prueba unitaria](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Puede seleccionar una o varias pruebas unitarias enumeradas en el Explorador de pruebas; a continuación, haga clic con el botón derecho y elija **Ejecutar pruebas seleccionadas**.
   >
   > Además, puede elegir **Depurar pruebas seleccionadas**, **Abrir prueba**y usar la opción **Propiedades** .
   >
   > ![Menú contextual de prueba unitaria del Explorador de pruebas unitarias](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   La prueba unitaria se ejecuta. Al finalizar, el Explorador de pruebas muestra el estado de la prueba y el tiempo transcurrido y proporciona un vínculo al origen.

   ![Explorador de pruebas unitarias: prueba completada](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Vea también

- [Prueba de aplicaciones para UWP con Visual Studio](../test/unit-test-your-code.md)
- [Compilar y probar una aplicación de UWP](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)