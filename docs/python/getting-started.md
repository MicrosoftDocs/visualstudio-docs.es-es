---
title: "Introducción a Python en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: e9a05d008f671fb79d6813a14c594b82f27697e3
ms.openlocfilehash: 2659c1a3b1adfc3f462971205460942c5fe5171f
ms.lasthandoff: 03/27/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>Introducción a Python en Visual Studio

Después de haber instalado Visual Studio con la carga de trabajo de Python (Visual Studio 2017) o con las Herramientas de Python para Visual Studio (Visual Studio 2015 y versiones anteriores), ya puede explorar la experiencia de desarrollo con Python.

En este tutorial, va a crear una nueva aplicación Python vacía, luego va a elegir un entorno Python con el que desea trabajar y, por último, va a empezar a escribir algo de código para ver IntelliSense en funcionamiento. A continuación, trabajará con la ventana interactiva de REPL durante poco tiempo para crear más código, luego completará el programa y lo ejecutará manualmente o en el depurador.

> [!Note]
> En este tutorial también se explora la experiencia de Python en Visual Studio 2017; las demás versiones serán similares, pero los detalles pueden variar.

## <a name="create-a-new-python-project"></a>Creación de un proyecto de Python nuevo

La compatibilidad de Python en Visual Studio incluye una serie de [plantillas de proyecto](python-projects.md) para comenzar con diferentes tipos de proyectos, incluidas aplicaciones web que usan los marcos Bottle, Flask y Django junto con Azure Cloud Services. Para los fines de este tutorial, sin embargo, comenzaremos con un proyecto vacío.

1. En Visual Studio, seleccione **Archivo > Nuevo proyecto** y después se abre el cuadro de diálogo **Nuevo proyecto**. Aquí puede examinar y seleccionar una plantilla y especificar la carpeta en la que desea crear el proyecto.

1. Las plantillas de Python se pueden encontrar en **Plantillas > Otros lenguajes > Python** en el lado izquierdo, o bien con tan solo buscar "Python":

    ![Cuadro de diálogo Nuevo proyecto con los proyectos de Python](media/getting-started-new-project.png)

1. Seleccione la plantilla "Python Application" (Aplicación de Python), especifique una carpeta para el proyecto y seleccione **Aceptar**. (Si desea crear un repositorio local para el proyecto justo ahora, seleccione también la opción **Agregar al control de código fuente**).

    > [!Tip]
    > La plantilla "From exiting Python Code" (A partir del código Python existente) permite crear rápidamente un proyecto de Visual Studio desde una carpeta que ya contiene código Python, en lugar de tener que crear un proyecto vacío nuevo e importar en él el código existente.

1. Después de unos minutos, verá el proyecto abierto en la ventana del Explorador de soluciones de Visual Studio. Aquí puede examinar los archivos y carpetas del proyecto, así como administrar entornos.

    ![Explorador de soluciones con un proyecto de Python](media/getting-started-solution-explorer-1.png)

1. Expanda el nodo **Python Environments** (Entornos de Python) y verá qué intérprete de Python es el predeterminado actualmente para este proyecto. Si expande también el nodo de ese intérprete, verá una lista de las bibliotecas disponibles en dicho entorno:

    ![Explorador de soluciones en el que se muestra el entorno de Python](media/getting-started-solution-explorer-2.png)

1. Si usa Visual Studio 2015 o versiones anteriores, no tendrá un intérprete de Python instalado de forma predeterminada. Vea [Selecting and installing Python interpreters](python-environments.md#selecting-and-installing-python-interpreters) (Selección e instalación de intérpretes de Python) para este proceso.

### <a name="going-deeper"></a>Mayor profundización

- [Python Projects in Visual Studio](python-projects.md) (Proyectos de Python en Visual Studio)
- [Plantillas de proyecto web](template-web.md)
- [Plantilla de proyecto web de Django](template-django.md)
- [Plantilla de servicio de nube de Azure](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>Escritura y ejecución de código

1. Después de crear un nuevo proyecto como "Aplicación de Python", se abre un archivo vacío predeterminado `PythonApplication1.py` en el editor de Visual Studio. Para cambiar el nombre, haga clic con el botón derecho en el archivo en el Explorador de soluciones y seleccione **Cambiar nombre** y después cambie el nombre por `hello.py`.

1. Comience a escribir `print("Hello world")` y observe cómo Visual Studio IntelliSense muestra las opciones de autocompletar mientras escribe. La opción destacada en la lista desplegable se corresponde con la versión predeterminada que se usaba al presionar la tecla TAB. Puede resultar muy útil cuando se trata de identificadores o instrucciones más largos.

    ![Ventana emergente de finalización automática de IntelliSense](media/getting-started-coding-1.png)

1. IntelliSense muestra información diferente en función de la instrucción utilizada, la función invocada, etc. Con función `print`, escriba `(` para invocar una ventana emergente con toda la información de uso de dicha función e incluso resalta en negrita el argumento actual que debe proporcionar (**value**, como se muestra aquí):

    ![Ventana emergente de finalización automática de IntelliSense para una función](media/getting-started-coding-2.png)

1. Complete la instrucción para que coincida con lo siguiente:

  ```python
  print("Hello world")
  ```

1. Para ejecutar el código, seleccione el botón **Iniciar** situado en la barra de herramientas que se muestra a continuación, presione F5 o seleccione el elemento de menú **Depurar > Iniciar depuración**.

    ![Botón de inicio en la barra de herramientas de depuración](media/getting-started-coding-3.png)

    > [!Note]
    > Si en Visual Studio 2015 o en versiones anteriores aparece un mensaje que indica que no hay intérpretes, vea [Selecting and installing Python interpreters](python-environments.md#selecting-and-installing-python-interpreters) (Selección e instalación de intérpretes de Python), en caso de que no haya ninguno instalado de forma predeterminada.

1. Visual Studio ejecutará el código con el entorno predeterminado del proyecto y mostrará los resultados en una ventana de comandos. Presione una tecla para cerrar la ventana y finalizar la sesión de depuración.

    ![Botón de inicio en la barra de herramientas de depuración](media/getting-started-coding-4.png)

1. Además de las instrucciones y funciones, IntelliSense proporciona finalizaciones para las instrucciones `import`. Esto ayuda a detectar fácilmente qué módulos se encuentran disponibles en el entorno y los miembros disponibles en ese módulo. En el editor, elimine la línea `print` y comience a escribir `import`. Aparecerá una lista de módulos:

    ![IntellSense muestra los módulos disponibles para una instrucción import](media/getting-started-coding-5.png)

1. Escriba o seleccione `sys` para completar la línea.

1. En la línea siguiente, escriba `from` para volver a ver una lista de módulos:

    ![IntellSense muestra los módulos disponibles para una instrucción from](media/getting-started-coding-6.png)

1. Seleccione o escriba `math`, luego agregue un espacio y `import`, para mostrar los miembros del módulo:

    ![IntellSense muestra los miembros del módulo](media/getting-started-coding-7.png)

1. Para terminar, importe los miembros `sin`, `cos` y `radians`, con las finalizaciones automáticas disponibles para cada uno de ellos. Cuando haya terminado, el código debería aparecer como sigue:

  ```python
  import sys  
  from math import sin, cos, radians          
  ```

> [!Tip]
> Las finalizaciones se activan con las subcadenas a medida que escribe, mostrando coincidencias con partes de palabras, letras al principio de las palabras e incluso caracteres omitidos. Vea [Editing Code - Completions](code-editing.md#completions) (Edición de código - Finalizaciones) para obtener información.

En el siguiente paso, vamos a trabajar con la ventana interactiva de REPL para escribir algún código que podemos probar inmediatamente sin ejecutar el depurador.

### <a name="going-deeper"></a>Mayor profundización

- [Edición de código](code-editing.md)
- [Formato de código](code-formatting.md)
- [Refactorización de código](code-refactoring.md)
- [Uso de PyLint](code-pylint.md)


## <a name="using-the-interactive-repl-window"></a>Uso de la ventana interactiva de REPL

La ventana interactiva de Visual Studio para Python proporciona una experiencia de lectura-evaluación-impresión-repetición que reduce considerablemente el ciclo habitual de edición-compilación-depuración. Es similar a la experiencia REPL de la línea de comandos de Python, pero proporciona algunas características adicionales, como verá a continuación.

1. Abra la ventana interactiva; para ello, seleccione **Ver > Otras ventanas > Ventanas interactivas de Python** en el menú principal de Visual Studio. Se abre la ventana con el indicador >>> habitual de REPL de Python. Tenga en cuenta que puede utilizar el menú desplegable de la barra de herramientas para cambiar el entorno en cualquier momento:

    ![Ventana interactiva de Python](media/getting-started-interactive-1.png)

1. Escriba algunas instrucciones (como `print("hello")`) y expresiones (como `123/567`) para ver los resultados inmediatos:

    ![Resultados inmediatos de la ventana interactiva de Python](media/getting-started-interactive-2.png)

1. Al empezar a escribir una instrucción multilínea, como una definición de función, en la ventana interactiva se muestra el símbolo ... para las líneas siguientes, que, a diferencia de la línea de comandos de REPL, proporciona una sangría automática:

    ![Ventana interactiva de Python con la continuación de la instrucción](media/getting-started-interactive-3.png)

1. La ventana interactiva proporciona un historial completo de todo lo que ha escrito y ofrece mejoras con respecto a la línea de comandos de REPL con elementos de historial multilínea. Por ejemplo, puede recuperar fácilmente la definición completa de la función `f` anterior como una única unidad y cambiar el nombre con facilidad a `make_double`, en lugar de tener que volver a crear la función línea por línea.

1. Otra característica muy útil es la capacidad de enviar rápidamente varias líneas de código desde una ventana del editor a la ventana interactiva, donde puede trabajar con el código en el entorno rápido de REPL en lugar de tener que escribir otro código para ejecutarlo en el depurador. Para ver esto, empiece por agregar el código siguiente al archivo hello.py que se abre en el editor:

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. Seleccione el código en hello.py (incluidas las instrucciones `import`), haga clic con el botón derecho y seleccione **Enviar a Interactive** (Ctrl+Enter). El código se pega inmediatamente en la ventana interactiva y se ejecuta. Dado que el código define una función, puede probarla rápidamente si la invoca varias veces:

    ![Envío de código a la ventana interactiva](media/getting-started-interactive-4.png)

1. **Enviar a Interactive** permite pegar de manera eficaz varias líneas de código (por ejemplo, algo que encuentre en línea) en la ventana interactiva, una acción que se puede realizar directamente. Por ejemplo, copie el código siguiente y trate de pegarlo (Ctrl+V) en la ventana interactiva y verá que no sucede nada. No obstante, puede pegarlo en el editor, seleccionarlo y usar el comando **Enviar a Interactive** para verlo en ejecución.

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![Pegar varias líneas de código mediante Enviar a Interactive](media/getting-started-interactive-5.png)

1. Dado que la definición de función vuelve a aparecer en el historial de REPL como una unidad única, puede volver atrás con facilidad para realizar los cambios deseados y probar la función de nuevo.

1. Cuando esté satisfecho con el código escrito, puede seleccionarlo en la ventana interactiva, hacer clic con el botón derecho, seleccionar **Copiar código** y pegarlo después en el editor. La característica especial del comando **Copiar código** consiste en que omite automáticamente cualquier salida y el texto de los símbolos >>> y .... Por ejemplo, al usar el comando con la selección siguiente:

  ![Comando Copiar código de la ventana interactiva](media/getting-started-interactive-6.png)

  se pegará solo lo siguiente:

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. Por último, la ventana interactiva proporciona una serie de metacomandos que permiten cargar archivos, restablecer el entorno sin perder el historial e insertar comentarios a medida que avanza. Vea [Interactive Windows - meta-commands](interactive-repl.md#meta-commands) (Ventanas interactivas - metacomandos) para obtener más información.

### <a name="going-deeper"></a>Mayor profundización

- [Uso de la ventana interactiva](interactive-repl.md)
- [Usar REPL de IPython](interactive-repl-ipython.md)

## <a name="running-code-in-the-debugger"></a>Ejecución de código en el depurador

Además de administrar proyectos, ofrecer una experiencia de edición enriquecida y la ventana interactiva, Visual Studio proporciona compatibilidad de depuración completa para el código Python.

1. Edite el código en el archivo hello.py para que coincida con lo siguiente:

  ```python  
  from math import sin, cos, radians  
  import sys  
    
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
    
  def main():  
      for i in range(360 * 5):
          s = make_dot_string(i)  
          print(s)  
            
  main()
  ```  

1. Compruebe que el código funciona correctamente; para ello, seleccione **Iniciar** en la barra de herramientas, presione F5 o seleccione el comando de menú **Depurar > Iniciar depuración**. Se ejecuta el código en el depurador, pero ya no hay ningún punto de interrupción establecido, simplemente observará que imprime un patrón ondulado para algunas iteraciones. Al presionar cualquier tecla, se cerrará la ventana de salida en ese punto.

    > [!Tip]
    > Para cerrar la ventana de salida automáticamente cuando se completa el programa, reemplace la llamada `main()` con el código siguiente:
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```
    > 
    > Como alternativa, si alguna vez se producen situaciones en las que la ventana de salida se cierra automáticamente cuando no le interesa que esto suceda, haga clic con el botón derecho en el proyecto, seleccione **Propiedades**, elija la pestaña **Depurar** y, después, agregue `-i` al campo **Argumentos del intérprete**. Esto hará que el intérprete entre en modo interactivo una vez que haya finalizado un programa, con lo que la ventana se mantendrá abierta hasta que pulse Ctrl+Z, ENTRAR para salir.

1. Establezca un punto de interrupción en la primera línea de la función `main`; para ello, haga clic en el margen gris de la izquierda de dicha línea, o bien coloque el operador exponencial en dicha línea y use el comando *Depurar > Alternar puntos de interrupción** (F9). Aparecerá un punto rojo en el margen gris para indicar el punto de interrupción (como indica la flecha azul a continuación):

    ![Establecer un punto de interrupción](media/getting-started-debugging-1.png)

1. Vuelva a iniciar el depurador y verá que, al ejecutar el código, se detiene en la línea en que se ha establecido el punto de interrupción. Aquí puede ver la pila de llamadas y examinar las variables locales en la ventana Variables locales:

    ![Experiencia de interfaz de usuario de puntos de interrupción para Python](media/getting-started-debugging-2.png)

1. Cambie entre algunas iteraciones del bucle `for` línea por línea; para ello, presione F10, use el comando **Depurar > Paso a paso por procedimiento** o presione el botón Paso a paso por procedimiento en la barra de herramientas. Esto significa que el depurador ejecutará cada llamada en `make_dot_string`, pero no se detendrá dentro de dicha función (a menos que defina un punto de interrupción).

1. En la barra de herramientas, los tres botones de ejecución paso a paso que se muestran a continuación, de izquierda a derecha, son: Paso a paso por instrucción, Paso a paso por procedimiento y Paso a paso para salir:

    ![Botones de ejecución paso a paso de la barra de herramientas](media/getting-started-debugging-3.png)

1. Ahora realice una ejecución paso a paso por instrucción de `make_dot_string` mediante el comando Paso a paso por instrucción (F11). Observará que realizará los pasos desde el bucle `for` hasta esa función. Si vuelve a realizar la ejecución paso a paso, volverá al bucle `for`, pero, si hay líneas adicionales en la función, pasará por ellas una a una. Si está en una función y desea ejecutar sus líneas restantes y volver al código de llamada, use Paso a paso para salir (Mayús+F11).

1. Para continuar ejecutando el código hasta llegar al próximo punto de interrupción (o hasta que el programa finalice), vuelva a presionar F5 o seleccione el botón de la barra de herramientas **Continuar** o **Depurar > Continuar**. Puesto que hay un punto de interrupción en el bucle `for`, la interrupción se producirá en la siguiente iteración.

1. Pasar por los centenares de iteraciones de un bucle puede resultar una tarea tediosa, por lo que puede agregar una condición al punto de interrupción establecido anteriormente para que la interrupción se produzca solo cuando el valor de `i` supere un valor concreto, es decir, 1600. Para ello, haga clic en el punto rojo del punto de interrupción y seleccione **Condición...** En la ventana Configuración del punto de interrupción que se abre, escriba `i > 1600` como expresión y seleccione **Cerrar**. Ahora presione F5 para continuar y verá que el programa se ejecuta durante un tiempo antes de interrumpirse de nuevo. 

    ![Definición de una condición de punto de interrupción](media/getting-started-debugging-4.png)

1. Para completar el programa, puede volver a alternar el punto de interrupción y presionar F5. Visual Studio vuelve al modo de edición cuando se completa la depuración.

### <a name="going-deeper"></a>Mayor profundización

- [Debugging](debugging.md) (Depuración).
- Vea también [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md) (Depuración en Visual Studio) para acceder a toda la documentación sobre las características de depuración de Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

Además de los vínculos proporcionados anteriormente en la sección "Mayor profundización", en los temas siguientes se tratan características adicionales de la experiencia de Python en Visual Studio:

- Para consultar cómo Visual Studio se conecta a Azure App Service, vea [Publishing a Python web application to Azure](publishing-to-azure.md) (Publicación de una aplicación web de Python en Azure).
- Para explorar cómo administrar entornos diferentes, tanto para proyectos globales como individuales, incluidos los entornos virtuales, vea [Python Environments](python-environments.md) (Entornos de Python).
- Visual Studio ofrece la posibilidad de depurar aplicaciones en servidores remotos, como se describe en [Cross-platform Remote Debugging](debugging-cross-platform-remote.md) (Depuración remota multiplataforma) y [Azure Remote Debugging](debugging-azure-remote.md) (Depuración remota en Azure).
- Puede evaluar el rendimiento del código Python según se describe en [Visual Studio Profiling](profiling.md) (Generación de perfiles en Visual Studio).
- Las pruebas unitarias escritas en Python se integran directamente con el Explorador de pruebas de Visual Studio, como se describe en [Unit Testing](unit-testing.md) (Pruebas unitarias).

