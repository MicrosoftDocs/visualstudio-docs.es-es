---
title: Crear un proyecto de rendimiento web y prueba de carga
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c6703221f9db06ca8edba68a2f2bcc9b79a5d531
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784753"
---
# <a name="quickstart-create-a-load-test-project"></a>Inicio rápido: Crear un proyecto de pruebas de carga

En este inicio rápido de 10 minutos, aprenderá a crear y ejecutar un proyecto de prueba de carga y rendimiento web en Visual Studio. Las pruebas de carga ejecutan pruebas unitarias o de rendimiento web para simular que muchos usuarios tienen acceso a un servidor al mismo tiempo.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Requisitos de software

Los proyectos de prueba de carga y rendimiento web solo están disponibles en la **edición Enterprise** de Visual Studio.

## <a name="install-the-load-testing-component"></a>Instalar el componente de prueba de carga

Si aún no tiene instalado el componente de herramientas de pruebas de carga y rendimiento web, deberá instalarlo con el Instalador de Visual Studio.

1. Abra el **Instalador de Visual Studio** desde el menú **Iniciar** de Windows. También puede tener acceso a él en Visual Studio desde el cuadro de diálogo de nuevo proyecto, o bien seleccionando **Herramientas** > **Get Tools and Features** (Obtener herramientas y características) en la barra de menús.

1. En el **Instalador de Visual Studio**, elija la pestaña **Componentes individuales** y desplácese hacia abajo hasta la sección **Depuración y pruebas**. Seleccione **Herramientas de rendimiento web y pruebas de carga**.

   ![Componente de herramientas de rendimiento web y pruebas de carga](media/web-perf-load-testing-tools-component.png)

1. Elija el botón **Modificar**.

   El componente de herramientas de rendimiento web y pruebas de carga se instala.

## <a name="create-a-load-test-project"></a>Crear un proyecto de pruebas de carga

En esta sección, vamos a crear un proyecto de prueba de carga de C#. También puede crear un proyecto de prueba de carga de Visual Basic, si lo prefiere.

::: moniker range="vs-2017"

1. Abra Visual Studio.

2. Elija **Archivo** > **Nuevo** > **Proyecto** en la barra de menús.

   Aparece el cuadro de diálogo **Nuevo proyecto** .

3. En el cuadro de diálogo **Nuevo proyecto**, expanda **Instalado** y **Visual C#** y, después, elija la categoría **Prueba**. Elija la plantilla **Proyecto de prueba de carga y rendimiento web**.

   ![Plantilla de proyecto de prueba de carga y rendimiento web](media/web-perf-load-test-project-template.png)

4. Escriba un nombre para el proyecto si no quiere usar el predeterminado y elija **Aceptar**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio.

2. En la ventana de inicio, elija **Crear un proyecto nuevo**.

3. En el cuadro de búsqueda de la página **Crear un proyecto**, escriba **prueba web** y seleccione la plantilla **Proyecto de prueba de carga y rendimiento web\[En desuso]** para C#. Seleccione **Siguiente**.

4. Escriba un nombre para el proyecto si no quiere usar el predeterminado y elija **Crear**.

::: moniker-end

   Visual Studio crea el proyecto y muestra los archivos en el **Explorador de soluciones**. Inicialmente, el proyecto contiene un archivo de prueba web denominado *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Agregar una prueba de carga al proyecto

1. En el menú contextual que aparece al hacer clic con el botón derecho en el nodo de proyecto en el **Explorador de soluciones**, elija **Agregar** > **Prueba de carga**.

   Se abre el **Asistente para prueba de carga nueva**.

1. Seleccione la opción **Prueba de carga local** y, después, elija **Siguiente**. [Aquí](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts) encontrará más información sobre las pruebas de carga basadas en la nube.

   ![Asistente para prueba de carga nueva: primera página](media/load-test-wizard-page-1.png)

1. Elija **Siguiente** para ir avanzando por el asistente hasta llegar a la página **Agregar pruebas a un escenario de prueba de carga y editar la combinación de pruebas**. Elija el botón de **Agregar** .

   Se abre el cuadro de diálogo **Agregar pruebas**.

1. En **Pruebas disponibles**, seleccione **WebTest1** y, después, seleccione la flecha derecha para pasarla al cuadro **Pruebas seleccionadas**. Elija el botón **Aceptar** .

   ![Cuadro de diálogo Agregar pruebas](media/add-tests-dialog-box.png)

1. De regreso al **Asistente para prueba de carga nueva**, elija el botón **Finalizar**.

   La prueba de carga se agrega al proyecto y el archivo de prueba de carga se abre en la ventana del editor.

## <a name="run-the-load-test"></a>Ejecutar la prueba de carga

Hemos creado una prueba de carga que no hace gran cosa, pero vamos a ejecutarla de todos modos.

En el menú contextual que aparece al hacer clic con el botón derecho en la prueba de carga que está abierta en el editor, elija **Ejecutar prueba de carga**.

![Menú Ejecutar prueba de carga](media/run-load-test.png)

La prueba de carga comienza a ejecutarse. En la ventana **Resultados de pruebas** aparece la prueba que está en curso y en la ventana del editor, el Analizador de pruebas de carga. Una vez finalizada la prueba (que no debe tardar más de cinco minutos si se han aceptado los valores predeterminados), se muestra un resumen en el editor. Puede elegir entre **Gráficos**, **Tablas** o **Detalle** para obtener información de distinta índole sobre los resultados de la prueba de carga.

![Ventana del Analizador de pruebas de carga](media/load-test-analyzer.png)

## <a name="next-steps"></a>Pasos siguientes

Ahora que hemos creado un sencillo proyecto de prueba de carga, el siguiente paso consiste en configurar los escenarios, los conjuntos de contadores y la configuración de la ejecución.

> [!div class="nextstepaction"]
> [Editar configuraciones de pruebas](edit-load-tests.md)
