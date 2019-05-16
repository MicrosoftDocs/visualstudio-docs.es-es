---
title: 'Tutorial: Escribir un visualizador en C# | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 190ada55d5f46d159c6765e9af83d672b654313d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688156"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Tutorial: Escribir un visualizador en C\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo escribir un visualizador sencillo con C#. El visualizador que creará en este tutorial muestra el contenido de una cadena mediante un cuadro de mensaje de formularios Windows Forms. Este sencillo visualizador de cadenas no es especialmente útil, pero muestra los pasos básicos que se deben seguir para crear visualizadores más útiles para otros tipos de datos.

> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, vaya al menú **Herramientas**, y elija **Importar y exportar configuraciones**. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

El código del visualizador debe colocarse en un archivo DLL, el cual será leído por el depurador. Por lo tanto, el primer paso es crear un proyecto de biblioteca de clases para el archivo DLL.

#### <a name="to-create-a-class-library-project"></a>Para crear un proyecto de biblioteca de clases

1. En el **archivo** menú, elija **New** y, a continuación, haga clic en **nuevo proyecto**.

2. En el **nuevo proyecto** cuadro de diálogo **tipo de proyecto**s, seleccione **Visual C#**.

3. En el **plantillas** , seleccione **biblioteca de clases**.

4. En el cuadro **Nombre**, escriba un nombre adecuado para la biblioteca de clases como, por ejemplo, MyFirstVisualizer.

5. Haga clic en **Aceptar**.

   Después de crear la biblioteca de clases, debe agregar una referencia a Microsoft.VisualStudio.DebuggerVisualizers.DLL, para poder utilizar las clases que allí se definen. No obstante, antes de agregar la referencia, debe cambiar los nombres de algunas clases para que sean significativos.

#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Para cambiar el nombre de Class1.cs y agregar Microsoft.VisualStudio.DebuggerVisualizers

1. En el **Explorador de soluciones**, haga clic con el botón derecho en Class1.cs y elija **Cambiar nombre** en el menú contextual.

2. Cambie el nombre Class1.cs por un nombre significativo, como DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cambia automáticamente la declaración de clase en DebuggerSide.cs para que coincida con el nuevo nombre del archivo.

3. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y después elija **Agregar referencia** en el menú contextual.

4. En el cuadro de diálogo **Agregar referencia**, en la ficha **.NET**, elija Microsoft.VisualStudio.DebuggerVisualizers.DLL.

5. Haga clic en **Aceptar**.

6. En DebuggerSide.cs, agregue la instrucción siguiente a las instrucciones `using`:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Ahora, ya está listo para crear el código del depurador. Éste es el código que se ejecuta dentro del depurador para mostrar la información que desea visualizar. En primer lugar hay que cambiar la declaración del objeto `DebuggerSide` para que herede de la clase base `DialogDebuggerVisualizer`.

#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Para heredar de DialogDebuggerVisualizer

1. En DebuggerSide.cs, vaya a la línea siguiente del código:

   ```csharp
   public class DebuggerSide
   ```

2. Cambie el código por:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` tiene un método abstracto (`Show`) que debe reemplazar.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Para reemplazar el método DialogDebuggerVisualizer.Show

- En `public class DebuggerSide`, agregue el siguiente **método:**

  ```csharp
  override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  El método `Show` contiene el código que verdaderamente crea el cuadro de diálogo del visualizador, u otra interfaz de usuario, y muestra la información que se ha pasado del depurador al visualizador. Es necesario agregar el código que crea el cuadro de diálogo y muestra la información. En este tutorial, se realizará este paso mediante un cuadro de mensaje de formularios Windows Forms. En primer lugar debe agregar una referencia y una instrucción `using` para System.Windows.Forms.

#### <a name="to-add-systemwindowsforms"></a>Para agregar System.Windows.Forms

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y después elija **Agregar referencia** en el menú contextual.

2. En el cuadro de diálogo **Agregar referencia**, en la ficha **.NET**, elija System.Windows.Forms.DLL.

3. Haga clic en **Aceptar**.

4. En DebuggerSide.cs, agregue la instrucción siguiente a las instrucciones `using`:

   ```csharp
   using System.Windows.Forms;
   ```

   Ahora, agregará código para crear y mostrar la interfaz de usuario para el visualizador. Debido que éste es su primer visualizador, mantendremos la interfaz de usuario sencilla y utilizaremos un cuadro de mensaje.

#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Para mostrar el resultado del visualizador en un cuadro de diálogo

1. En el método `Show`, agregue la siguiente línea de código:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    En este código de ejemplo no se incluye el control de errores. Debe incluir el control de errores en un visualizador real o en cualquier otro tipo de aplicación.

2. En el menú **Compilar**, elija **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   Ése es el fin del código del depurador. Sin embargo, hay un paso más que realizar; el atributo que indica al lado depurado qué colección de clases incluye el visualizador.

#### <a name="to-add-the-debuggee-side-code"></a>Para agregar el código que está siendo depurado

1. Agregue el código de atributo siguiente a DebuggerSide.cs, después de las instrucciones `using`, pero antes de `namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target  = typeof(System.String),
   Description  = "My First Visualizer")]
   ```

2. En el menú **Compilar**, elija **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   En este momento, el primer visualizador está terminado. Si ha seguido los pasos correctamente, debería poder compilar el visualizador e instalarlo en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sin embargo, antes de instalar un visualizador en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], debería probarlo para asegurarse de que se ejecuta correctamente. A continuación creará un instrumento de prueba para ejecutar el visualizador sin instalarlo en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Para agregar un método de prueba para mostrar el visualizador

1. Agregue el método siguiente a la clase `public DebuggerSide`:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. En el menú **Compilar**, elija **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   Luego, debe crear un proyecto ejecutable para llamar al archivo DLL del visualizador. Por simplicidad, utilizaremos un proyecto de aplicación de consola.

#### <a name="to-add-a-console-application-project-to-the-solution"></a>Para agregar un proyecto de aplicación de consola a la solución

1. En el menú **Archivo**, elija **Agregar** y después haga clic en **Nuevo proyecto**.

2. En el **Agregar nuevo proyecto** cuadro de diálogo el **plantillas** , seleccione **aplicación de consola**.

3. En el cuadro **Nombre**, escriba un nombre significativo para la aplicación de consola, como `MyTestConsole`.

4. Haga clic en **Aceptar**.

   Ahora, debe agregar las referencias necesarias para que MyTestConsole pueda llamar a MyFirstVisualizer.

#### <a name="to-add-necessary-references-to-mytestconsole"></a>Para agregar las referencias necesarias a MyTestConsole

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y elija **Agregar referencia** en el menú contextual.

2. En el cuadro de diálogo **Agregar referencia**, en la ficha **.NET**, elija Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Haga clic en **Aceptar**.

4. Haga clic con el botón derecho en **MyTestConsole** y elija nuevamente **Agregar referencia**.

5. En el cuadro de diálogo **Agregar referencia**, haga clic en la ficha **Proyectos** y después haga clic en MyFirstVisualizer.

6. Haga clic en **Aceptar**.

   A continuación, agregará el código para finalizar el instrumento de prueba.

#### <a name="to-add-code-to-mytestconsole"></a>Para agregar el código a MyTestConsole

1. En el **Explorador de soluciones**, haga clic con el botón derecho en Program.cs y elija **Cambiar nombre** en el menú contextual.

2. Cambie el nombre Program.cs por un nombre más significativo, como TestConsole.cs.

    **Tenga en cuenta** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cambia automáticamente la declaración de clase de TestConsole.cs para que coincida con el nuevo nombre de archivo.

3. En TestConsole.cs, agregue el siguiente código a las instrucciones `using`:

   ```csharp
   using MyFirstVisualizer;
   ```

4. En el método `Main`, agregue el código siguiente:

   ```
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Ahora, está listo para probar el primer visualizador.

#### <a name="to-test-the-visualizer"></a>Para probar el visualizador

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y, en el menú contextual, elija **Establecer como proyecto de inicio**.

2. En el menú **Depurar**, elija **Iniciar**.

    Se iniciará la aplicación de consola y aparecerá el visualizador, que mostrará la cadena "Hello, World".

   Enhorabuena. Acaba de compilar y probar el primer visualizador.

   Si desea utilizar el visualizador en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], en lugar de simplemente llamarlo desde el instrumento de prueba, tendrá que instalarlo. Para obtener más información, vea [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md).

## <a name="using-the-visualizer-item-template"></a>Utilizar la plantilla de elementos del visualizador
 Hasta ahora, en este tutorial se ha mostrado cómo crear manualmente un visualizador. Esto se realizó como un ejercicio de aprendizaje. Ahora que sabe cómo funciona un visualizador sencillo, existe una manera más fácil de crear uno: mediante la plantilla de elementos del visualizador.

 En primer lugar, debe crear un nuevo proyecto de biblioteca de clases.

#### <a name="to-create-a-new-class-library"></a>Para crear una nueva biblioteca de clases

1. En el menú **Archivo**, elija **Agregar** y después haga clic en **Nuevo proyecto**.

2. En el **Agregar nuevo proyecto** cuadro de diálogo **tipo de proyecto**s, seleccione **Visual C#**.

3. En el **plantillas** , seleccione **biblioteca de clases**.

4. En el cuadro **Nombre**, escriba un nombre adecuado para la biblioteca de clases como, por ejemplo, MySecondVisualizer.

5. Haga clic en **Aceptar**.

   A continuación, puede agregarle un elemento del visualizador:

#### <a name="to-add-a-visualizer-item"></a>Para agregar un elemento del visualizador

1. En el **Explorador de soluciones**, haga clic con el botón derecho en MySecondVisualizer.

2. En el menú contextual, elija **Agregar** y después haga clic en **Nuevo elemento**.

3. En el **Agregar nuevo elemento** cuadro de diálogo **plantillas**, **plantillas instaladas de Visual Studio**, seleccione **visualizador del depurador**.

4. En el cuadro **Nombre**, escriba un nombre adecuado, como SecondVisualizer.cs.

5. Haga clic en **Agregar**.

   Eso es todo lo que tiene que hacer. Examine el archivo SecondVisualizer.cs y observe el código que la plantilla ha agregado por usted. Continúe y experimente con el código. Ahora que conoce los fundamentos, ya puede crear visualizadores más complejos y útiles.

## <a name="see-also"></a>Vea también

- [Arquitectura de un visualizador](../debugger/visualizer-architecture.md)
- [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
