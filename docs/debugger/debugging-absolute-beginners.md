---
title: Código de depuración para principiantes sin experiencia
description: Si depura por primera vez, obtenga información sobre algunos principios que le ayudarán a ejecutar la aplicación en modo de depuración con Visual Studio.
ms.date: 07/06/2018
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ff3f2552f2334d87bc329bab41501570bd67864
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918214"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Cómo depurar para principiantes sin experiencia

Sin excepción, el código que escriben los desarrolladores de software no siempre hace lo que se espera. A veces hace algo completamente diferente. Cuando esto sucede, la siguiente tarea consiste en averiguar por qué y, aunque podríamos vernos tentados a quedarnos mirando fijamente nuestro código durante horas, es mucho más fácil y eficaz que use una herramienta de depuración, o depurador.

Un depurador, lamentablemente, no puede revelar todos los problemas o “errores” en nuestro código mágicamente. *Depurar* significa ejecutar el código paso a paso en una herramienta de depuración como Visual Studio, para buscar el punto exacto donde ha cometido un error de programación. Entonces sabrá qué correcciones debe realizar en el código; las herramientas de depuración suelen permitir realizar cambios temporales para que pueda continuar la ejecución del programa.

Usar un depurador de forma eficaz también es una habilidad que lleva tiempo y práctica desarrollar, pero en última instancia es una tarea fundamental para los desarrolladores de software. En este artículo se presentan los principios básicos de la depuración y se proporcionan sugerencias para ayudarle a comenzar.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Aclarar el problema haciéndose las preguntas adecuadas

Resultará útil aclarar el problema que surgió antes de intentar corregirlo. Se supone que ya haya tenido algún problema con el código porque, en caso contrario, no debería estar intentando averiguar cómo depurarlo. Por lo tanto, antes de iniciar la depuración, asegúrese de que ha identificado el problema que está intentando resolver:

* ¿Qué esperaba que hiciese el código?

* ¿Qué pasó en su lugar?

    Si se produjo un error (excepción) durante la ejecución de la aplicación, podría ser algo bueno. Una excepción es un evento inesperado al ejecutar código, normalmente un error de algún tipo. Una herramienta de depuración puede llevarle hasta el lugar exacto en el código donde se produjo la excepción y puede ayudarle a investigar las posibles soluciones.

    Si ha sucedido otra cosa, ¿cuál es el síntoma del problema? ¿Ya sospecha que este problema se produjo en el código? Por ejemplo, si el código muestra algo de texto, pero el texto es incorrecto, sabe que los datos son incorrectos o el código que establece el texto para mostrar tiene algún tipo de error. Al pasar el código por un depurador, puede examinar cada uno de los cambios en las variables para descubrir exactamente cuándo y cómo se asignaron valores incorrectos.

## <a name="examine-your-assumptions"></a>Examinar sus suposiciones

Antes de investigar un error, piense en las suposiciones que le llevaron a esperar un resultado determinado. Suposiciones ocultas o desconocidas pueden interponerse a la hora de identificar un problema incluso cuando está mirando a la causa del problema en un depurador. Es posible que tenga una larga lista de suposiciones posibles. Estas son algunas preguntas con las que puede cuestionar sus suposiciones.

* ¿Está usando la API adecuada (es decir, el objeto, función, método o propiedad adecuado)? Una API que esté usando podría no hacer lo que piensa que hace. (Después de examinar la llamada API en el depurador, para corregirla puede ser necesario consultar la documentación para ayudar a identificar la API correcta).

* ¿Está utilizando una API correctamente? Tal vez ha usado la API correcta pero no la usó de la forma adecuada.

* ¿El código contiene errores al escribir? Algunos errores tipográficos, como un error al escribir un nombre de variable, pueden ser difíciles de ver, especialmente cuando se trabaja con idiomas que no requieren que se declaren las variables antes de usarse.

* ¿Realizó un cambio en el código y supone que no está relacionado con el problema que está viendo?

* ¿Esperaba que un objeto o una variable contuviese un valor determinado (o un determinado tipo de valor) que es diferente de lo que realmente sucedió?

* ¿Conoce la intención del código? A menudo resulta más difícil de depurar el código de otra persona. Si no es su propio código, es posible que deba dedicar tiempo a conocer qué hace exactamente el código antes de poder depurarlo de forma eficaz.

    > [!TIP]
    > Al escribir código, empiece poco a poco y con el código que funciona. (Un buen código de ejemplo puede ser útil aquí). A veces, resulta más fácil de corregir un conjunto grande o complejo de código empezando con un pequeño fragmento de código que muestra la tarea principal que está intentando lograr. Después, puede modificar o agregar código de forma incremental, haciendo pruebas en cada punto en busca de errores.

Al cuestionar sus suposiciones, puede reducir el tiempo necesario para encontrar un problema en el código. También puede reducir el tiempo necesario para corregir un problema.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Recorrer el código en modo de depuración para buscar dónde se produjo el problema

Al ejecutar una aplicación con normalidad, verá errores y resultados incorrectos solo después de que se haya ejecutado el código. Un programa también puede finalizarse inesperadamente sin que se indique por qué.

Ejecutar una aplicación dentro de un depurador, también denominado *modo de depuración*, significa que el depurador supervisa activamente todo lo que sucede durante la ejecución del programa. También permite pausar la aplicación en cualquier momento para examinar su estado y después recorrer el código línea por línea para ver todos los detalles a medida que se produce.

En Visual Studio, puede entrar en el modo de depuración mediante **F5** (o el comando de menú **Depurar** > **Iniciar depuración** o el botón **Iniciar depuración** ![Start Debugging](../debugger/media/dbg-tour-start-debugging.png "Start Debugging") de la barra de herramientas Depurar). Si se produce alguna excepción, el Asistente de excepciones de Visual Studio le lleva al punto exacto donde ocurrió y proporciona información útil adicional. Para más información sobre cómo controlar las excepciones en el código, vea [Técnicas y herramientas de depuración](../debugger/write-better-code-with-visual-studio.md).

Si no recibió una excepción, probablemente pueda hacerse una idea de dónde buscar el problema en el código. Aquí es donde usará *puntos de interrupción* con el depurador para examinar más detenidamente el código. Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe pausar la ejecución de código para poder echar un vistazo a los valores de las variables, al comportamiento de la memoria o a la secuencia en la que se ejecuta el código.

En Visual Studio, puede configurar rápidamente un punto de interrupción haciendo clic en el margen izquierdo junto a una línea de código. También puede colocar el cursor en una línea y presionar **F9**.

Para ayudar a ilustrar estos conceptos, le llevaremos por código de ejemplo que ya tiene varios errores. Estamos usando C#, pero las características de depuración se aplican a Visual Basic, C++, JavaScript, Python y otros lenguajes compatibles.

### <a name="create-a-sample-app-with-some-bugs"></a>Crear una aplicación de ejemplo (con algunos errores)

A continuación, crearemos una aplicación que tiene algunos errores.

1. Debe tener instalado Visual Studio y las cargas de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo multiplataforma de .NET Core**, según el tipo de aplicación que quiera crear.

    Si todavía no ha instalado Visual Studio, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  para instalarlo de forma gratuita.

    Si tiene que instalar la carga de trabajo pero ya tiene Visual Studio, haga clic en **Herramientas** > **Obtener herramientas y características**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de escritorio de .NET** (o la carga de trabajo **Desarrollo multiplataforma de .NET Core**) y después haga clic en **Modificar**.

1. Abra Visual Studio, y después elija **Archivo** > **Nuevo** > **Proyecto**.

1. Elija una plantilla para el código de aplicación.

    Para .NET Framework, en el cuadro de diálogo **Nuevo proyecto**, elija **Visual C#**, **Windows Desktop** desde la sección Plantillas instaladas y después, en el panel central, seleccione **Aplicación de consola (.NET Framework)**.

    Para .NET Core, en el cuadro de diálogo **Nuevo proyecto**, elija **Visual C#**, **.NET Core** desde la sección Plantillas instaladas y después, en el panel central, seleccione **Aplicación de consola (.NET Core)**.

    Si no ve estas plantillas, debe instalar la carga de trabajo adecuada (consulte los pasos anteriores).

1. En el campo **Nombre**, escriba **ConsoleApp-FirstApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto de consola, con lo que aparece el Explorador de soluciones (en el panel derecho).

1. En *Program.cs*, reemplace todo el código predeterminado con el código siguiente:

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

    Nuestra intención para este código es mostrar la información del nombre de la galaxia, la distancia a la galaxia y el tipo de galaxia en una lista. Para depurar, es importante comprender la intención del código. Este es el formato de una línea en la lista que se va a mostrar en la salida:

    *nombre de la galaxia*, *distancia*, *tipo de galaxia*.

### <a name="run-the-app"></a>Ejecutar la aplicación

1. Presione **F5** o el botón **Iniciar depuración** ![Iniciar depuración](../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración") en la barra de herramientas Depuración, situada sobre el editor de código.

    La aplicación se inicia y el depurador no nos muestra ninguna excepción. Sin embargo, la salida que se ve en la ventana de consola no es la esperada. Este es el resultado esperado:

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    No obstante, en su lugar vemos esto:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Si nos fijamos en la salida y en nuestro código, sabemos que `GType` es el nombre de la clase que almacena el tipo de galaxia. Estamos intentando mostrar el tipo de galaxia real (por ejemplo, “espiral”), no el nombre de clase.

### <a name="debug-the-app"></a>Depurar la aplicación

1. Con la aplicación ejecutándose, establezca un punto de interrupción haciendo clic en el margen izquierdo junto a la llamada al método `Console.WriteLine` en esta línea de código.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Cuando establece el punto de interrupción, aparece un punto rojo en el margen izquierdo.

    Dado que se detecta un problema en la salida, comenzaremos la depuración examinando el código anterior que establece la salida en el depurador.

1. Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas Depuración (**Ctrl** + **Mayús**  +  **F5**).

    La aplicación se detiene en el punto de interrupción que definió. El resaltado amarillo indica que el depurador está en pausa (la línea amarilla de código aún no se ha ejecutado).

1. Mantenga el mouse sobre la variable `GalaxyType` a la derecha y después, a la izquierda del icono de llave inglesa, expanda `theGalaxy.GalaxyType`. Verá que `GalaxyType` contiene una propiedad `MyGType` y el valor de propiedad se establece en `Spiral`.

    ![Inspeccionar una variable](../debugger/media/beginners-inspect-variable.png)

    “Espiral” es realmente el valor correcto que se esperaba que se imprimiese en la consola. Por lo tanto, es un buen punto de partida que pueda tener acceso a este valor en el código mientras se ejecuta la aplicación. En este escenario, usamos la API incorrecta. Veremos si podemos corregir esto mientras se ejecuta código en el depurador.

1. En el mismo código, mientras todavía se depura, coloque el cursor al final de `theGalaxy.GalaxyType` y cámbielo a `theGalaxy.GalaxyType.MyGType`. Aunque puede realizar este cambio, el editor de código muestra un error que indica que no puede compilar este código.

    ![Error de sintaxis](../debugger/media/beginners-edit.png)

1. Haga clic en **Editar** en el cuadro de mensaje **Editar y continuar**. Ahora verá un mensaje de error en la ventana **Lista de errores**. El error indica que el `'object'` no contiene una definición para `MyGType`.

    ![Error de sintaxis](../debugger/media/beginners-no-definition.png)

    Aunque se establezca cada galaxia con un objeto de tipo `GType` (que tiene la propiedad `MyGType`), el depurador no reconoce el objeto `theGalaxy` como un objeto de tipo `GType`. ¿Qué sucede? Desea buscar cualquier código que establece el tipo de galaxia. Al hacerlo, verá que la clase `GType` definitivamente tiene una propiedad de `MyGType`, pero algo no es correcto. El mensaje de error sobre `object` resulta ser la pista; para el intérprete de lenguaje, el tipo parece ser un objeto de tipo `object` en lugar de un objeto de tipo `GType`.

1. Al examinar el código relacionado con la configuración del tipo galaxia, descubre que la propiedad `GalaxyType` de la clase `Galaxy` está especificada como `object` en lugar de `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Cambiar el código anterior a este:

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas de depuración (**Ctrl** + **Mayús**  +  **F5**) para volver a compilar el código y reiniciar.

    Ahora, cuando el depurador se detiene en `Console.WriteLine`, puede mantener el puntero sobre `theGalaxy.GalaxyType.MyGType` y ver que el valor se estableció correctamente.

1. Quite el punto de interrupción haciendo clic en el círculo de punto de interrupción en el margen izquierdo (o haga clic con el botón derecho y elija **Punto de interrupción** > **Eliminar punto de interrupción**) y después presione **F5** para continuar.

    La aplicación se ejecuta y muestra el resultado. Ahora tiene bastante buen aspecto, pero tenga en cuenta una cosa; esperaba que la galaxia Pequeña Nube de Magallanes apareciese como una galaxia irregular en la salida de consola, pero no muestra ningún tipo de galaxia en absoluto.

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

    Este código es donde se establece el tipo de galaxia, por lo que queremos analizarlo en detalle.

1. Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas de depuración (**Ctrl** + **Mayús**  +  **F5**) para reiniciar.

    El depurador se detiene en la línea de código en la que estableció el punto de interrupción.  

1. Mantenga el mouse sobre la variable `type`. Ve un valor de `S` (siguiendo el código de carácter). Le interesa un valor de `I`, dado que usted sabe que es un tipo de galaxia irregular.

1. Presione **F5** y mantenga de nuevo el mouse sobre la variable `type`. Repita este paso hasta que vea un valor de `I` en la variable `type`.

    ![Inspeccionar una variable](../debugger/media/beginners-inspecting-data.png)

1. Ahora, presione **F11** (**Depurar** > **Depurar paso a paso por instrucciones** o el botón **Depurar paso a paso por instrucciones** en la barra de herramientas Depuración).

    **F11** hace avanzar el depurador (y ejecuta código) en una instrucción cada vez. **F10** (**Saltar**) es un comando similar y ambos son extremadamente útiles para aprender a usar el depurador.

1. Presione **F11** hasta que se detenga en la línea de código en la instrucción `switch` para un valor de “I”. En este caso, verá un problema claro causado por un error de escritura. Esperaba que el código avanzase a donde se establece `MyGType` como un tipo de galaxia irregular, pero en su lugar el depurador omite completamente este código y se detiene en la sección `default` de la instrucción `switch`.

    ![Encontrar un error de escritura](../debugger/media/beginners-typo.png)

    Examinando el código, ve un error de escritura en la instrucción `case 'l'`. Debería ser `case 'I'`.

1. Haga clic en el código para `case 'l'` y reemplácelo por `case 'I'`.

1. Quite el punto de interrupción y después haga clic en el botón **Reiniciar** para reiniciar la aplicación.

    Ahora están corregidos los errores y verá la salida esperada.

    Presione cualquier tecla para finalizar la aplicación.

## <a name="summary"></a>Resumen

Cuando vea un problema, utilice el depurador y los [comandos de paso](../debugger/navigating-through-code-with-the-debugger.md) como **F10** y **F11** para buscar la región de código con el problema.

> [!NOTE]
> Si es difícil identificar la región de código donde se produce el problema, establezca un punto de interrupción en código que se ejecuta antes de que se produce el problema y después use los comandos de paso hasta que vea el problema manifiesto. También puede usar [puntos de seguimiento](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) para registrar mensajes en la ventana **Salida**. Al mirar los mensajes registrados (y observar los mensajes que aún no se registraron), a menudo puede aislar la región de código con el problema. Es posible que deba repetir este proceso varias veces para delimitarla.

Cuando encuentre la región de código con el problema, utilice el depurador para investigar. Para averiguar la causa de un problema, inspeccione el código del problema mientras se ejecuta la aplicación en el depurador:

* [Inspeccione variables](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) y compruebe si contienen el tipo de valores que deben contener. Si encuentra un valor incorrecto, averigüe dónde se estableció el valor no válido (para buscar dónde se estableció el valor, es posible que deba reiniciar el depurador, examinar la [pila de llamadas](../debugger/how-to-use-the-call-stack-window.md) o realizar ambas acciones).

* Compruebe si la aplicación está ejecutando el código que espera. (Por ejemplo, en la aplicación de ejemplo, se esperaba que el código de la instrucción de conmutador estableciese el tipo de galaxia en irregular, pero la aplicación omitió el código debido al error de escritura).

> [!TIP]
> Use un depurador para ayudarle a encontrar errores. Una herramienta de depuración puede encontrar errores *automáticamente* solo si conoce la intención del código. Una herramienta solo puede saber la intención del código si usted, la persona que desarrolla, expresa dicha intención. Puede hacerlo escribiendo [pruebas unitarias](../test/improve-code-quality.md). 

## <a name="next-steps"></a>Pasos siguientes

En este artículo, ha aprendido algunos conceptos generales de depuración. A continuación, puede empezar a aprender más sobre el depurador.

> [!div class="nextstepaction"]
> [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
