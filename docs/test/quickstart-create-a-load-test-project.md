---
title: Creación de un proyecto de prueba de carga y rendimiento web en Visual Studio
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 4349220f650eef98ee765c1e7dbacb69263fe845
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976720"
---
# <a name="quickstart-create-a-load-test-project"></a>Inicio rápido: Crear un proyecto de prueba de carga

En este inicio rápido de 10 minutos, aprenderá a crear y ejecutar un proyecto de prueba de carga y rendimiento web en Visual Studio. Las pruebas de carga ejecutan pruebas unitarias o de rendimiento web para simular que muchos usuarios tienen acceso a un servidor al mismo tiempo.

> [!IMPORTANT]
> Los proyectos de prueba de carga y rendimiento web solo están disponibles en la edición Enterprise de Visual Studio 2017.

## <a name="install-the-load-testing-component"></a>Instalar el componente de prueba de carga

Si aún no tiene instalado el componente de herramientas de pruebas de carga y rendimiento web, deberá instalarlo con el Instalador de Visual Studio.

1. Abra el Instalador de Visual Studio desde el menú Inicio. También puede tener acceso a él en Visual Studio desde el cuadro de diálogo **Nuevo proyecto**, o bien seleccionando **Herramientas** > **Obtener herramientas y características...** en la barra de menús.

1. En el Instalador de Visual Studio, elija la pestaña **Componentes individuales** y desplácese hacia abajo hasta la sección **Depuración y pruebas**. Seleccione **Herramientas de rendimiento web y pruebas de carga**.

   ![Componente de herramientas de rendimiento web y pruebas de carga](media/web-perf-load-testing-tools-component.png)

1. Elija el botón **Modificar**.

   El componente de herramientas de rendimiento web y pruebas de carga se instala.

## <a name="create-a-load-test-project"></a>Crear un proyecto de pruebas de carga

En esta sección, vamos a crear un proyecto de prueba de carga de C#. También puede crear un proyecto de prueba de carga de Visual Basic, si lo prefiere.

1. Abra Visual Studio y seleccione **Archivo** > **Nuevo** > **Proyecto...** en la barra de menús.

   Aparece el cuadro de diálogo **Nuevo proyecto** .

1. En el cuadro de diálogo **Nuevo proyecto**, expanda **Instalado** y **Visual C#** y, después, elija la categoría **Prueba**. Elija la plantilla **Proyecto de prueba de carga y rendimiento web**.

   ![Plantilla de proyecto de prueba de carga y rendimiento web](media/web-perf-load-test-project-template.png)

1. Escriba un nombre para el proyecto si no quiere usar el predeterminado y elija **Aceptar**.

   Visual Studio crea el proyecto y muestra los archivos en el **Explorador de soluciones**. Inicialmente, el proyecto contiene un archivo de prueba web denominado *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Agregar una prueba de carga al proyecto

1. En el menú contextual que aparece al hacer clic con el botón derecho en el nodo de proyecto en el **Explorador de soluciones**, elija **Agregar** > **Prueba de carga...**

   Se abre el **Asistente para prueba de carga nueva**.

1. Seleccione la opción **Prueba de carga local** y, después, elija **Siguiente**. [Aquí](/vsts/load-test/get-started-simple-cloud-load-test) encontrará más información sobre las pruebas de carga basadas en la nube.

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