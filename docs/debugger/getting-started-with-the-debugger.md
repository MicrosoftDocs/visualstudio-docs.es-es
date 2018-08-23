---
title: Obtenga información sobre cómo depurar con el depurador de Visual Studio
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 235e9386070d316cd9a4f9751ac1d8f1e8fd92b4
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2018
ms.locfileid: "42623789"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Tutorial: Información sobre cómo depurar con Visual Studio

En este artículo se presenta las características del depurador de Visual Studio en un tutorial paso a paso. Si desea una vista de nivel superior de las características del depurador, vea [Guía de características del depurador](../debugger/debugger-feature-tour.md). Cuando se *depurar la aplicación*, suele significar que se ejecuta la aplicación con el depurador adjunto. Al hacerlo, el depurador proporciona muchas formas de ver lo que hace el código mientras se ejecuta. Puede ver los valores almacenados en variables y recorrer el código, puede establecer inspecciones de variables para ver cuando cambian los valores, puede examinar la ruta de acceso de ejecución del código, vea si una bifurcación de código está en funcionamiento, y así sucesivamente. Si se trata de la primera vez que ha probado para depurar el código, es posible que desea leer [de depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) antes de pasar a través de este artículo.

|         |         |
|---------|---------|
|  ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo")  |    [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sobre la depuración que muestran los mismos pasos. |

Aunque la aplicación de demostración es C# y C++, las características son aplicables a Visual Basic, JavaScript y otros lenguajes compatibles con Visual Studio (excepto donde se indique). Las capturas de pantalla se encuentran en C#. Para cambiar entre el código de ejemplo de C++ y C#, use el filtro de lenguaje en la esquina superior derecha de la página.

En este tutorial va a:

> [!div class="checklist"]
> * Iniciar al depurador y alcanzar puntos de interrupción.
> * Obtenga información sobre los comandos para recorrer el código en el depurador
> * Inspeccionar las variables en las sugerencias de datos y las ventanas del depurador
> * Examinar la pila de llamadas

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio 2017 y el **desarrollo de escritorio de .NET** o **desarrollo de escritorio con C++** carga de trabajo.

    Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

    Si necesita instalar la carga de trabajo pero ya tiene Visual Studio, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto** (seleccione **Archivo** > **Nuevo** > **Proyecto**). Se iniciará el Instalador de Visual Studio. Elija el. **El desarrollo de escritorio neto** o **desarrollo de escritorio con C++** carga de trabajo, a continuación, elija **modificar**.

## <a name="create-a-project"></a>Crear un proyecto

1. En Visual Studio, seleccione **Archivo > Nuevo proyecto**.

2. En **Visual C#** o **Visual C++**, elija **Windows Desktop**y, a continuación, en el panel central, elija **aplicación de consola** ( **Aplicación de consola Windows** en C++).

    Si no ve el **aplicación de consola** plantilla de proyecto, haga clic en el **abrir Visual Studio Installer** vínculo en el panel izquierdo de la **nuevo proyecto** cuadro de diálogo. Se iniciará el Instalador de Visual Studio. Elija la *desarrollo de escritorio de .NET** o **desarrollo de escritorio con C++** carga de trabajo, a continuación, elija **modificar**.

3. Escriba un nombre como **get-iniciado-depuración** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

4. En *Program.cs* (C#) o *debugging.cpp iniciado get* (C++), reemplace el código siguiente

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    ```c++
    int main()
    {
        return 0;
    }
    ```

    con este código:

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }
   
        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }

    }

    /* Output:
        Drawing a rectangle
        Performing base class drawing tasks
        Drawing a triangle
        Performing base class drawing tasks
        Drawing a circle
        Performing base class drawing tasks
    */
    ```

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
        }
    }

    /* Output:
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>Iniciar al depurador.

1. Presione **F5** (**Depurar > Iniciar depuración**) o el **Iniciar depuración** botón ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración ") en la barra de herramientas de depuración.

     **F5** inicia la aplicación con el depurador se adjunta a la aplicación procesar, pero en este momento no hemos hecho nada especial para examinar el código. Por lo que solo carga la aplicación y ver la salida de consola.

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     En este tutorial, obtendrá tomamos una aproximación a esta aplicación con el depurador y obtener las características de un vistazo en el depurador.

2. Detenga el depurador presionando el delimitador de color rojo ![Detener depuración](../debugger/media/dbg-tour-stop-debugging.png "Detener depuración") botón.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Establecer un punto de interrupción e iniciar el depurador

1. En el `foreach` bucle de la `Main` función (`for` bucle en C++ `main` función), establezca un punto de interrupción, haga clic en el margen izquierdo de la primera línea de código.

    ![Establezca un punto de interrupción](../debugger/media/get-started-set-breakpoint.png "SetABreakPoint")

    Aparece un círculo rojo en las que establecer el punto de interrupción.

    Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código. 

6. Presione **F5** o **Iniciar depuración** botón, la aplicación se inicia y se ejecuta el depurador a la línea de código donde estableció el punto de interrupción.

    ![Alcanzar un punto de interrupción](../debugger/media/get-started-hit-breakpoint.png "HitABreakPoint")

    La flecha amarilla representa la instrucción en el que el depurador está en pausa, que también suspende la ejecución de la aplicación en el mismo punto (esta instrucción no se ha ejecutado).

     Si aún no se ejecuta la aplicación, **F5** inicia el depurador y se detiene en el primer punto de interrupción. En caso contrario, **F5** continúa ejecutando la aplicación para el punto de interrupción siguiente.

    Puntos de interrupción son una característica muy útil cuando se sabe que la línea de código o en la sección de código que desea examinar con detalle.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegar por el código en el depurador mediante comandos de paso

Principalmente, usamos los métodos abreviados de teclado en este caso, porque es una buena forma de obtener rápida al ejecutar la aplicación en el depurador (comandos equivalentes como menú de comandos se muestran entre paréntesis).

1. Presione **F11** (o elija **Depurar > paso a paso**) una vez (varias veces en C#) hasta que se hace una pausa sobre la `shape.Draw` llame al método el `Main` método (`shape->Draw` en C++).

1. Presione **F11** una vez más para avanzar en el código para el `Rectangle` clase.

     ![Use F11 para depurar paso a paso el código](../debugger/media/get-started-f11.png "paso a paso F11")

     F11 es el **paso a paso** comando y hace avanzar la una instrucción ejecución de aplicación a la vez. F11 es una buena manera para examinar el flujo de ejecución en el nivel más detallado. (Para mover más rápido a través del código, le mostraremos algunas otras opciones también.) De forma predeterminada, el depurador omite el código de no usuario (si desea obtener más información, consulte [solo mi código](../debugger/just-my-code.md)).

2. Presione **F10** (o elija **Depurar > saltar**) varias veces hasta que el depurador se detiene en el `base.Draw` llamada al método (`Shape::Draw` en C++) y, a continuación, presione **F10** Una vez más.

     ![Use F10 para el código paso a paso por](../debugger/media/get-started-step-over.png "saltar F10")

     Tenga en cuenta esta vez que el depurador no entra en el `Draw` método de la clase base (`Shape`). **F10** hace avanzar el depurador sin entrar en las funciones o métodos en el código de aplicación (todavía se ejecuta el código). Al presionar F10 en el `base.Draw` (o `Shape::Draw`) llamada al método (en lugar de **F11**), se omite el código de implementación de `base.Draw` (que probablemente nos no estamos interesados en este momento).

## <a name="navigate-code-using-run-to-click"></a>Navegar por el código mediante la ejecución, haga clic en

5. En el editor de código, desplácese hacia abajo y mantenga el mouse sobre el `Console.WriteLine` método (`std::cout` en C++) en el `Triangle` clase hasta que el verde **hacer clic y ejecutar** botón ![hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click.png " RunToClick") aparece a la izquierda.

     ![Use la ejecución, haga clic en características](../debugger/media/get-started-run-to-click.png "hacer clic y ejecutar")

    >  [!NOTE]
    > El **hacer clic y ejecutar** es nuevo en el botón [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Si no ve el botón de flecha verde, use **F11** en este ejemplo en su lugar para avanzar el depurador al lugar correcto.

6. Haga clic en el **hacer clic y ejecutar** botón ![hacer clic y ejecutar](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Mediante este botón es similar a la configuración de un punto de interrupción temporal. **Hacer clic y ejecutar** es útil para desplazarse rápidamente dentro de un área visible del código de la aplicación (puede hacer clic en cualquier archivo abierto).

    El depurador avanza a la `Console.WriteLine` implementación del método para el `Triangle` clase (`std::cout` en C++).

    Mientras está en pausa, verá un error de escritura. La salida "Dibujar un trangle" está mal escrita. Podemos corregir justo mientras se ejecuta la aplicación en el depurador.

## <a name="edit-code-and-continue-debugging"></a>Editar código y seguir depurando

1. Haga clic en "Dibujar un trangle" y escriba una corrección, cambiando "trangle" a "triangle".

1. Presione **F11** una vez y verá que el depurador avanza de nuevo.

    > [!NOTE]
    > Dependiendo de qué tipo de código edita en el depurador, verá un mensaje de advertencia. En algunos escenarios, el código tendrá que volver a compilar antes de continuar.

## <a name="step-out"></a>Salir

Supongamos que se realiza examinando la `Draw` método en el `Triangle` clase y desea sacar partido de la función, pero permanecen en el depurador. Puede hacerlo mediante el **paso a paso fuera** comando.

1. Presione **MAYÚS** + **F11** (o **Depurar > Salir**).

     Este comando reanuda la ejecución de la aplicación (y hace avanzar el depurador) hasta que devuelve la función actual.

     Debería estar en el `foreach` bucle en el `Main` método (`for` bucle en C++).

## <a name="restart-your-app-quickly"></a>Reinicie la aplicación rápidamente

Haga clic en el **reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") botón en la barra de herramientas Depurar (**Ctrl** + **MAYÚS**   +  **F5**).

Al presionar **reiniciar**, ahorra tiempo en comparación con la aplicación de detener y reiniciar el depurador. El depurador se detiene en el primer punto de interrupción que se obtiene acceso mediante la ejecución de código.

El depurador se detiene de nuevo en el punto de interrupción establecido, en el `foreach` bucle (`for` bucle en C++).

## <a name="inspect-variables-with-data-tips"></a>Inspeccionar las variables con sugerencias de datos

Las características que permiten inspeccionar las variables son una de las características más útiles del depurador, y hay diferentes maneras de hacerlo. A menudo, cuando se intenta depurar un problema, está intentando averiguar si las variables almacena los valores que se esperan que tengan en un momento determinado.

1. Mientras está en pausa en el `foreach` bucle (`for` bucle en C++), presione **F11** una vez.

1. Mantenga el mouse sobre el `shapes` objeto y ver su valor de propiedad predeterminado, el `Count` propiedad.

1. Expanda el `shapes` objeto para ver todas sus propiedades, como el primer índice de la matriz `[0]`, que tiene un valor de `Rectangle` (C#) o una dirección de memoria (C++).

     ![Ver información sobre datos](../debugger/media/get-started-data-tip.png "ver una sugerencia de datos")

    A menudo, cuando se depura, desea que una forma rápida de comprobar los valores de propiedad en objetos, y las sugerencias de datos son una buena forma de hacerlo.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspeccionar las variables con las ventanas automático y variables locales

1. Examine el **automático** ventana en la parte inferior del editor de código.

     ![Inspeccionar las variables en la ventana automático](../debugger/media/get-started-autos-window.png "ventana automático")

    En el **automático** ventana, puede ver las variables y su valor actual. El **automático** ventana muestra todas las variables usadas en la línea actual o la línea anterior (en C++, la ventana muestra las variables en las tres líneas de código anteriores. Consulte la documentación para el comportamiento específico del idioma).

    > [!NOTE]
    > En JavaScript, la **variables locales** pero no se admite la ventana de la **automático** ventana.

2. A continuación, examine el **variables locales** ventana, en una pestaña situada junto a la **automático** ventana.

    El **variables locales** ventana muestra las variables que se encuentran en el actual [ámbito](https://www.wikipedia.org/wiki/Scope_(computer_science)).

## <a name="set-a-watch"></a>Establece una inspección

1. En la ventana del editor de código principal, haga clic en el `shapes` de objetos y elija **Agregar inspección**.

    El **inspección** se abre una ventana en la parte inferior del editor de código. Puede usar un **inspección** ventana para especificar una variable (o una expresión) que desee vigilar en.

    Ahora, tendrá una inspección establecida en el `shapes` objeto y puede ver su valor cambia conforme se desplaza por el depurador. A diferencia de las otras ventanas de variables, la **inspección** ventana siempre muestra las variables que está viendo (están atenuadas cuando fuera del ámbito).

## <a name="examine-the-call-stack"></a>Examinar la pila de llamadas

1. Mientras está en pausa en el `foreach` bucle (`for` bucle en C++), haga clic en el **pila de llamadas** ventana, que está abierto en el panel inferior derecho de forma predeterminada.

1. Haga clic en **F11** varias veces hasta que vea que el depurador pausa en el `Circle.Draw` método en el editor de código. Examine el **pila de llamadas** ventana.

    ![Examinar la pila de llamadas](../debugger/media/get-started-call-stack.png "ExamineCallStack")

    El **pila de llamadas** ventana muestra el orden en el que obtener se llaman los métodos y funciones. La línea superior muestra la función actual (la `Circle.Draw` o `Circle::Draw` método en esta aplicación). La segunda línea muestra que `Circle.Draw` se llamó desde el `Main` método (`main` en C++), y así sucesivamente.

    >  [!NOTE]
    > El **pila de llamadas** ventana es similar a la perspectiva de depuración de algunos IDE como Eclipse.

    La pila de llamadas es una buena manera para examinar y entender el flujo de ejecución de una aplicación.

    Haga doble clic en una línea de código para ir a mirar ese código fuente y que también cambia el ámbito actual va a inspeccionar el depurador. Esta acción no hace avanzar al depurador.

    También puede usar los menús contextuales de la **pila de llamadas** ventana hacer otras cosas. Por ejemplo, puede insertar puntos de interrupción en funciones especificadas, avanzar el depurador mediante **ejecutar hasta el Cursor**y vaya a examinar el código fuente. Para obtener más información, consulte [Cómo: examinar la pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Cambiar el flujo de ejecución

1. Con el depurador en pausa en el `Circle.Draw` llamada al método, presione **F11** varias veces hasta que el depurador se detiene en el `base.Draw` llamada al método (`Shape::Draw` en C++).

1. Use el mouse para captar la flecha amarilla (el puntero de ejecución) a la izquierda y mover la flecha amarilla hacia arriba una línea a la `Console.WriteLine` (`std::cout` en C++) llamada de método.

1. Presione **F11** una vez más.

    El depurador vuelve a ejecutar el `Console.WriteLine` método (`std::cout` en C++).

    Al cambiar el flujo de ejecución, puede hacer cosas como comprobar las rutas de ejecución de código diferente o volver a ejecutar código sin necesidad de reiniciar al depurador.

    > [!WARNING]
    > A menudo es necesario tener cuidado con esta característica, y verá una advertencia en la información sobre herramientas. Puede ver otras advertencias, demasiado. Mover el puntero no puede revertir la aplicación a un estado anterior de la aplicación.

1. Presione **F5** para seguir ejecutando la aplicación.

    Enhorabuena por completar este tutorial.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo iniciar al depurador, paso a través del código e inspeccionar las variables. Es posible que desee obtener un alto nivel sobre las características del depurador junto con vínculos para obtener más información.

> [!div class="nextstepaction"]
> [Guía de características del depurador](../debugger/debugger-feature-tour.md)
