---
title: Depurar C++
description: Depure código nativo con el depurador de Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ee57fe4d2df3a9d1fa9f4f8a624e7b63caa1f7fd
ms.sourcegitcommit: 8d453b345c72339c37b489a140dad00b244e6ba4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2019
ms.locfileid: "58475960"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Inicio rápido: Depurar con C++ mediante el depurador de Visual Studio

El depurador de Visual Studio proporciona muchas características de gran eficacia para ayudar a depurar aplicaciones. En este tema se proporciona una forma rápida de obtener información sobre las características básicas.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo

1. Abra Visual Studio y cree un proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **c++**, elija **Plantillas** y luego, **Crear proyecto de aplicación de consola**. En el cuadro de diálogo que se abre, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual C++**, elija **Escritorio de Windows** y luego, en el panel central, **Aplicación de consola Windows**. Luego escriba un nombre como **MyDbgApp** y haga clic en **Aceptar**.
    ::: moniker-end

    Si no ve la plantilla de proyecto **Aplicación de consola Windows**, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el Instalador de Visual Studio. Se iniciará el Instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

    Visual Studio crea el proyecto.

1. En MyDbgApp.cpp, reemplace el código siguiente

    ```c++
    int main()
    {
        return 0;
    }
    ```

    con este código (no quite `#include "stdafx.h"`):

    ```c++
    #include <list>
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción

Un *punto de interrupción* es un marcador que indica en qué punto debe Visual Studio suspender la ejecución de código para poder echar un vistazo a los valores de variables, o al comportamiento de memoria, o si se está ejecutando o no una rama de código. Es la característica más básica de la depuración.

1. Para establecer el punto de interrupción, haga clic en el medianil de la izquierda de la llamada a la función `doWork` (o seleccione la línea de código y presione **F9**).

    ![Establecimiento de un punto de interrupción](../debugger/media/dbg-qs-set-breakpoint.png "Set a breakpoint")

2. Ahora presione **F5** (o elija **Depurar > Iniciar depuración**).

    ![Llegada a un punto de interrupción](../debugger/media/dbg-qs-hit-breakpoint.png "Hit a breakpoint")

    El depurador se detiene donde se ha establecido el punto de interrupción. La instrucción donde se ha detenido la ejecución del depurador y la aplicación se indica mediante la flecha amarilla. La línea con la llamada a la función `doWork` aún no se ha ejecutado.

    > [!TIP]
    > Si tiene un punto de interrupción en un bucle o recursión, o si tiene muchos puntos de interrupción que ejecuta paso a paso con frecuencia, use un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) para asegurarse de que el código se suspende ÚNICAMENTE cuando se cumplen determinadas condiciones. Un punto de interrupción condicional ahorra tiempo y además puede facilitar la depuración de problemas que son difíciles de reproducir.

    Al intentar depurar errores relacionados con la memoria en C++, también puede usar puntos de interrupción para inspeccionar valores de dirección (busque NULL) y números de referencia.

## <a name="navigate-code"></a>Navegación en el código

Hay distintos comandos para indicar al depurador que continúe. Aquí se muestra un comando de navegación de código muy útil disponible a partir de Visual Studio 2017.

Mientras la ejecución está detenida en el punto de interrupción, mantenga el puntero sobre la instrucción `c1.push_back(20)` hasta que aparezca el botón verde **Run to click** (Ejecutar hasta clic) ![Ejecutar hasta clic](../debugger/media/dbg-tour-run-to-click.png "RunToClick") y luego presione el botón **Ejecutar hasta clic**.

![Ejecutar hasta clic](../debugger/media/dbg-qs-run-to-click.png "Run to click")

La aplicación se sigue ejecutando, llama a `doWork` y se detiene en la línea de código donde se ha hecho clic en el botón.

Los comandos de teclado habituales usados para ejecutar el código paso a paso son **F10** y **F11**. Para obtener instrucciones más detalladas, vea [Primer vistazo al depurador](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspeccionar las variables de una información sobre datos

1. En la línea de código actual (marcada con el puntero de ejecución amarillo), mantenga el puntero sobre el objeto `c1` para mostrar una información sobre datos.

    ![Visualización de una información sobre datos](../debugger/media/dbg-qs-data-tip.png "View a datatip")

    La información sobre datos muestra el valor actual de la variable `c1` y permite inspeccionar sus propiedades. Al depurar, si ve un valor que no esperaba, probablemente tenga un error en las líneas de código anteriores o de llamada.

2. Expanda la información sobre datos para ver los valores de propiedad actuales del objeto `c1`.

3. Si quiere anclar la información sobre datos para poder seguir viendo el valor de `c1` mientras ejecuta el código, haga clic en el icono de anclar pequeño. (Puede mover la información sobre datos anclada a una ubicación que le resulte cómoda).

## <a name="edit-code-and-continue-debugging"></a>Editar código y seguir depurando

Si identifica un cambio que quiere probar en el código a mitad de una sesión de depuración, también puede hacerlo.

1. Haga clic en la segunda instancia de `c2.front()` y cambie `c2.front()` por `c2.back()`.

2. Presione **F10** (o **Depurar > Saltar**) varias veces para que el depurador avance y ejecute el código editado.

    ![Editar y continuar](../debugger/media/dbg-qs-edit-and-continue.gif "Edit and continue")

    **F10** hace que el depurador avance de instrucción en instrucción, pero que se salte las funciones en lugar de depurarlas (el código que se omite se sigue ejecutando).

Para obtener más información sobre el uso de Editar y continuar y las limitaciones de las características, vea [Editar y continuar](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a iniciar el depurador, a ejecutar el código paso a paso y a inspeccionar variables. Puede ser que le interese analizar las características del depurador con más detenimiento, así como consultar los vínculos disponibles con más información.

> [!div class="nextstepaction"]
> [Guía de características del depurador](../debugger/debugger-feature-tour.md)
