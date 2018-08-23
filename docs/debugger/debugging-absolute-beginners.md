---
title: Depuración de código para principiantes absolutos
description: Si se depura por primera vez, obtenga información sobre algunos principios para ayudarle a ejecutar la aplicación en modo de depuración con Visual Studio
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb37faa194e3c370f92f9a82c7866373dd8f26d3
ms.sourcegitcommit: a6734c4d76dae3d21b55b10f3bc618dfa6b62dea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2018
ms.locfileid: "42623660"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Cómo depurar para principiantes absolutos

Sin errores, el código que escribimos los desarrolladores de software no siempre hace lo que esperábamos. ¡A veces hace algo completamente diferente! Cuando esto sucede, la siguiente tarea consiste en averiguar por qué y, aunque se podría verse tentados a simplemente mantener queden mirando fijamente nuestro código durante horas, es mucho más fácil y eficaz para que use una herramienta de depuración o del depurador.

Un depurador, Lamentablemente, no es algo que mágicamente puede revelar todos los problemas o "errores" en nuestro código. *Depuración* significa para ejecutar el código paso a paso en una herramienta de depuración como Visual Studio, para buscar el punto exacto donde ha cometido un error de programación. A continuación, sabrá qué correcciones se deba realizar en el código y las herramientas de depuración a menudo le permiten realizar cambios temporales para que pueda continuar la ejecución del programa.

Uso de un depurador eficaz también es una habilidad que lleva tiempo y práctica para aprender, pero en última instancia es una tarea fundamental para desarrolladores de software. En este artículo, a continuación, se presentan los principios básicos de depuración y proporcionan sugerencias para ayudarle a comenzar.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Aclarar el problema haciéndose las preguntas adecuadas

Ayuda a aclarar el problema que surgió antes de intentar corregirlo. Esperamos que ya se ejecutó en un problema en el código, en caso contrario, es no esté aquí intentando averiguar cómo depurarla! Por lo tanto, antes de iniciar la depuración, asegúrese de que haya identificado el problema que está intentando resolver:

* ¿Qué esperaba el código para hacer?

* ¿Qué ha ocurrido en su lugar?

    Si produjo un error (excepción) durante la ejecución de la aplicación, que puede ser una buena opción. Una excepción es un evento inesperado al ejecutar código, normalmente un error de algún tipo. Una herramienta de depuración puede tardar hasta el lugar exacto en el código donde se produjo la excepción y puede ayudarle a investigar las posibles soluciones.

    Si ha sucedido algo más, ¿qué es el síntoma del problema? ¿Ya sospecha que este problema se produjo en el código? Por ejemplo, si el código muestra parte del texto, pero el texto es incorrecto, sabe que los datos están incorrectos o el código que establece el texto para mostrar tiene algún tipo de error. Al recorrer el código en un depurador, puede examinar cada uno de los cambios a las variables para descubrir exactamente cuándo y cómo se asignan valores incorrectos.

## <a name="examine-your-assumptions"></a>Examine sus suposiciones

Antes de investigar un error o un error, piense en las suposiciones que realizan espera un resultado determinado. Suposiciones ocultas o desconocidas pueden interponerse que identifica un problema incluso cuando se trata de derecha a la causa del problema en un depurador. Es posible que tiene una larga lista de supuestos posibles. Estas son algunas preguntas para formular para cuestione sus hipótesis.

* ¿Está usando la API adecuada (es decir, el objeto derecho, función, método o propiedad)? Una API que esté usando podría no hacer lo que piensa que lo hace. (Después de examinar la llamada de API en el depurador, corregirlo requieran un viaje a la documentación para ayudar a identificar la API correcta.)

* ¿Está utilizando una API correctamente? Tal vez usa la API de la derecha pero no usarlo en la forma adecuada.

* ¿El código contiene errores al escribir? Algunos errores tipográficos, como un error ortográfico simple de un nombre de variable, pueden ser difíciles de ver, especialmente cuando se trabaja con idiomas que no requieren las variables se declaren antes de usarse.

* ¿Se realiza un cambio en el código y se supone que está relacionado con el problema que está viendo?

* ¿Se esperaba un objeto o una variable para contener un valor determinado (o un determinado tipo de valor) que es diferente de lo que realmente sucedió?

* ¿Conoce la intención del código? A menudo resulta más difícil de depurar que otra persona del código. Si no es el código, es posible que deberá dedicar tiempo a conocer hace exactamente lo que el código antes de poder depurar de forma eficaz.

    > [!TIP]
    > Al escribir código, empiece poco a poco y comenzar con el código que funciona! (Código de ejemplo buena resulta útil aquí.) A veces, resulta más fácil de corregir un conjunto grande o complejo de código al empezar con un pequeño fragmento de código que muestra la tarea principal que está intentando lograr. A continuación, puede modificar o agregar código de forma incremental, las pruebas en cada punto de errores.

Por sus suposiciones para hacer preguntas, puede reducir el tiempo necesario para encontrar un problema en el código. También puede reducir el tiempo necesario para corregir un problema.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Recorrer el código en modo para buscar dónde se produjo el problema de depuración

Al ejecutar una aplicación con normalidad, verá errores y resultados incorrectos solo después de que se ha ejecutado el código. Un programa también puede finalizar inesperadamente sin que se indica por qué.

Ejecutar una aplicación dentro de un depurador, también denominado *modo de depuración*, significa que el depurador supervisa activamente todo lo que sucede durante la ejecución del programa. También permite pausar la aplicación en cualquier momento para examinar su estado y, a continuación, recorrer el código línea por línea para ver todos los detalles a medida que se produce.

En Visual Studio, escriba el modo de depuración mediante **F5** (o la **depurar** > **Iniciar depuración** comando de menú o el **Iniciar depuración**  botón ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración")) en la barra de herramientas Depurar. Si se produce ninguna excepción, aplicación auxiliar de excepciones de Visual Studio le lleva al punto exacto donde ocurrió la excepción y proporciona otra información útil.

Si no recibió una excepción, probablemente tenga una buena idea dónde buscar el problema en el código. Esto dónde usas *puntos de interrupción* con el depurador para el Concédase una oportunidad para examinar más detenidamente el código. Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe pausar la ejecución de código para que pueda sacar un vistazo a los valores de variables, o el comportamiento de la memoria o la secuencia en que se ejecuta el código.

En Visual Studio, puede configurar rápidamente un punto de interrupción, haga clic en el margen izquierdo junto a una línea de código. O bien coloque el cursor en una línea y presione **F9**.

Para ayudar a ilustrar estos conceptos, se le llevan por el código de ejemplo que ya tiene varios errores. Estamos usando C#, pero las características de depuración aplican a Visual Basic, C++, JavaScript, Python y otros lenguajes compatibles.

### <a name="create-a-sample-app-with-some-bugs"></a>Crear una aplicación de ejemplo (con algunos errores)

A continuación, crearemos una aplicación que tiene algunos errores.

1. Debe tener instalado Visual Studio y, o bien el. **El desarrollo de escritorio neto** carga de trabajo o. **.NET Core, el desarrollo multiplataforma** carga de trabajo instalada, según el tipo de qué aplicación desea crear.

    Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

    Si tiene que instalar la carga de trabajo pero ya tiene Visual Studio, haga clic en **herramientas** > **obtener herramientas y características**. Se iniciará el Instalador de Visual Studio. Elija el. **El desarrollo de escritorio neto** (o. **.NET Core, el desarrollo multiplataforma**) carga de trabajo, a continuación, elija **modificar**.

1. Abra Visual Studio y, a continuación, elija **archivo** > **New** > **proyecto**.

1. Elija una plantilla para el código de aplicación.

    Para .NET Framework, en el **nuevo proyecto** diálogo cuadro, elija **Visual C#**, **Windows Desktop** desde la sección Plantillas instaladas y, a continuación, en el panel central, seleccione  **Aplicación de consola (.NET Framework)**.

    Para .NET Core, en el **nuevo proyecto** diálogo cuadro, elija **Visual C#**, **.NET Core** desde la sección Plantillas instaladas y, a continuación, en el panel central seleccione  **(.NET Core) de la aplicación de consola**.

    Si no ve estas plantillas, debe instalar la carga de trabajo adecuado (consulte los pasos anteriores).

1. En el **nombre** , escriba **ConsoleApp FirstApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto de consola, que aparece en el Explorador de soluciones en el panel derecho.

1. En *Program.cs*, reemplace todo el código predeterminado por el código siguiente:

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Es nuestra intención de este código mostrar el nombre de galaxy, la distancia a galaxy y el tipo de galaxy todo en una lista. Para depurar, es importante comprender la intención del código. Este es el formato de una línea en la lista que se va a mostrar en la salida:

    *nombre de Galaxy*, *distancia*, *tipo galaxy*.

### <a name="run-the-app"></a>Ejecutar la aplicación

1. Presione **F5** o **Iniciar depuración** botón ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración") en la barra de herramientas de depuración, que se encuentra encima del editor de código.

    La aplicación se inicia y no hay ninguna excepción se muestra a nosotros el depurador. Sin embargo, la salida que se ve en la ventana de consola es no es el esperado. Este es el resultado esperado:

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Sin embargo, vemos esto en su lugar:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Busca en la salida y en nuestro código, sabemos que `GType` es el nombre de la clase que almacena el tipo de galaxy. Estamos intentando muestran el tipo de galaxy real (por ejemplo, "espiral"), no el nombre de clase.

### <a name="debug-the-app"></a>Depurar la aplicación

1. Con la aplicación sigue ejecutándose, establezca un punto de interrupción haciendo clic en el margen izquierdo junto a la `Console.WriteLine` llamada al método en esta línea de código.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Al establecer el punto de interrupción, aparece un punto rojo en el margen izquierdo.

    Dado que se detecta un problema en la salida, comenzaremos la depuración si examina el código anterior que establece la salida en el depurador.

1. Haga clic en el **reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") botón en la barra de herramientas Depurar (**Ctrl** + **MAYÚS**   +  **F5**).

    La aplicación se detiene en el punto de interrupción que estableció. El resaltado amarillo indica que el depurador está en pausa (la línea amarilla de código aún no ejecutado).

1. Mantenga el mouse sobre el `GalaxyType` variable a la derecha y, a continuación, a la izquierda del icono de llave inglesa, expanda `theGalaxy.GalaxyType`. Verá que `GalaxyType` contiene una propiedad `MyGType`, y el valor de propiedad se establece en `Spiral`.

    ![Inspeccionar una variable](../debugger/media/beginners-inspect-variable.png)

    "Espiral" es realmente el valor correcto esperados para imprimir en la consola. Por lo que es un buen punto de partida que puede tener acceso a este valor en este código mientras se ejecuta la aplicación. En este escenario, usamos la API incorrecta. Veremos si podemos corregir esto mientras ejecuta código en el depurador.

1. En el mismo código, mientras se depura todavía, coloque el cursor al final de `theGalaxy.GalaxyType` y cámbiela a `theGalaxy.GalaxyType.MyGType`. Aunque puede realizar este cambio, el editor de código muestra un error que indica que no puede compilar este código.

    ![Error de sintaxis](../debugger/media/beginners-edit.png)

1. Haga clic en **editar** en el **editar y continuar** cuadro de mensaje. Vea un mensaje de error ahora en el **lista de errores** ventana. El error indica que el `'object'` no contiene una definición para `MyGType`.

    ![Error de sintaxis](../debugger/media/beginners-no-definition.png)

    Aunque se establezca cada galaxy con un objeto de tipo `GType` (que tiene el `MGType` propiedad), el depurador no reconoce el `theGalaxy` objeto como un objeto de tipo `GType`. ¿Qué pasa? Desea buscar a través de cualquier código que establece el tipo de galaxy. Al hacerlo, verá que el `GType` clase definitivamente tiene una propiedad de `MyGType`, pero algo no es correcto. El mensaje de error sobre `object` resulta para ser la pista; al intérprete de lenguaje, el tipo aparece como un objeto de tipo `object` en lugar de un objeto de tipo `GType`.

1. Examinar el código relacionados con la configuración del tipo galaxy, busque el `GalaxyType` propiedad de la `Galaxy` está especificada como `object` en lugar de `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Cambiar el código anterior a este:

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Haga clic en el **reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") botón en la barra de herramientas Depurar (**Ctrl** + **MAYÚS**   +  **F5**) para compilar el código y reiniciar.

    Ahora, cuando el depurador se detiene en `Console.WriteLine`, puede mantener el puntero sobre `theGalaxy.GalaxyType.MyGType`y verá que el valor se establece correctamente.

1. Quitar el punto de interrupción haciendo clic en el círculo de punto de interrupción en el margen izquierdo (o haga clic en y elija **punto de interrupción** > **Eliminar punto de interrupción**) y, a continuación, presione **F5** para continuar.

    La aplicación se ejecuta y muestra el resultado. Parece bastante bien ahora, pero tenga en cuenta una cosa; espera galaxy pequeña nube Magellanic aparezcan como una galaxia Irregular en la salida de consola, pero no muestra ningún tipo galaxy en absoluto.

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Establezca un punto de interrupción en esta línea de código.

    ```csharp
    public GType(char type)
    ```

    Este código es donde se establece el tipo de galaxy, por lo que queremos Eche un vistazo más de cerca en él.

1. Haga clic en el **reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") botón en la barra de herramientas Depurar (**Ctrl** + **MAYÚS**   +  **F5**) para reiniciar.

    El depurador se detiene en la línea de código donde estableció el punto de interrupción.  

1. Mantenga el mouse sobre el `type` variable. Ver un valor de `S` (siguiendo el código de carácter). Está interesado en un valor de `I`, dado que usted sabe que es un tipo de galaxy irregulares.

1. Presione **F5** y mantenga el mouse sobre el `type` variable nuevo. Repita este paso hasta que vea un valor de `I` en el `type` variable.

    ![Inspeccionar una variable](../debugger/media/beginners-inspecting-data.png)

1. Ahora, presione **F11** (**depurar** > **paso a paso** o **paso a paso** botón en la barra de herramientas de depuración).

    **F11** hace avanzar el depurador (y ejecuta código) en una instrucción a la vez. **F10** (**saltar**) es un comando similar y ambos son extremadamente útiles para aprender a usar el depurador.

1. Presione **F11** hasta que se detenga en la línea de código en el `switch` instrucción para un valor de 'I'. En este caso, verá un problema al borrar procedente de un error de escritura. Espera el código para avanzar a dónde se establece `MyGType` como un irregulares tipo galaxy, pero el depurador en su lugar, omite completamente este código y se detiene en el `default` sección de la `switch` instrucción.

    ![Encontrar un error de escritura](../debugger/media/beginners-typo.png)

    Examinar el código, verá un error de escritura en el `case 'l'` instrucción. Debe ser `case 'I'`.

1. Haga clic en el código para `case 'l'` y reemplácela por `case 'I'`.

1. Quite el punto de interrupción y, a continuación, haga clic en el **reiniciar** botón reiniciar la aplicación.

    Se corrigieron los errores ahora y verá la salida que espera.

    Presione cualquier tecla para finalizar la aplicación.

## <a name="summary"></a>Resumen

Cuando vea un problema, utilice el depurador y [paso comandos](../debugger/navigating-through-code-with-the-debugger.md) como **F10** y **F11** para buscar la región de código con el problema.

> [!NOTE]
> Si es difícil identificar la región de código donde se produce el problema, establezca un punto de interrupción en código que se ejecuta antes de que se produce el problema y, a continuación, use los comandos de paso hasta que vea el problema manifiesto. También puede usar [puntos de seguimiento](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) para registrar mensajes a la **salida** ventana. Por mirar los mensajes registrados (y observar los mensajes que no se registraron aún), a menudo puede aislar la región de código con el problema. Es posible que deba repetir este proceso varias veces para reducirlo.

Cuando encuentre la región de código con el problema, utilice al depurador para investigar. Para averiguar la causa de un problema, inspeccione el código del problema mientras se ejecuta la aplicación en el depurador:

* [Inspeccionar variables](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) y comprobar si contienen el tipo de valores que deben contener. Si encuentra un valor incorrecto, puede averiguar donde se estableció el valor no válido (para buscar dónde se estableció el valor, es posible que deba ser reiniciar el depurador, examine el [pila de llamadas](../debugger/how-to-use-the-call-stack-window.md), o ambos).

* Compruebe si la aplicación se está ejecutando el código que espera. (Por ejemplo, en la aplicación de ejemplo, se esperaba el código de la instrucción switch establecer el tipo de galaxy a irregulares, pero la aplicación omitió el código porque el error de escritura.)

> [!TIP]
> Use un depurador que le ayudarán a encontrar errores. Una herramienta de depuración puede encontrar errores *automáticamente* solo si conoce la intención del código. Una herramienta solo puede saber la intención del código si a los desarrolladores, expresa dicha intención. Escribir [pruebas unitarias](../test/improve-code-quality.md) es cómo hacerlo.

## <a name="next-steps"></a>Pasos siguientes

En este artículo, ha aprendido algunos conceptos generales de depuración. A continuación, puede empezar a aprender a depurar con Visual Studio.

> [!div class="nextstepaction"]
> [Guía de características del depurador](../debugger/debugger-feature-tour.md)
