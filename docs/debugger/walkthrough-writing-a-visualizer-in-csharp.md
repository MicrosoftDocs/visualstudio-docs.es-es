---
title: Escritura de un visualizador en C# | Microsoft Docs
description: Siga un tutorial para crear un visualizador simple en C#. Muestra los pasos necesarios con y sin la plantilla de elemento del visualizador.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 47c7fa8eaa5a735f05b338101a1aefe0601e9915
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298292"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Tutorial: Escritura de un visualizador en C\#

En este tutorial se muestra cómo escribir un visualizador sencillo con C#. El visualizador que creará en este tutorial muestra el contenido de una cadena mediante un formulario de Windows. Este sencillo visualizador de cadenas no es especialmente útil, pero muestra los pasos básicos que se deben seguir para crear visualizadores más útiles para otros tipos de datos.

> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, vaya al menú **Herramientas**, y elija **Importar y exportar configuraciones**. Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

El código del visualizador debe colocarse en un archivo DLL, el cual será leído por el depurador. Por lo tanto, el primer paso es crear un proyecto de biblioteca de clases para el archivo DLL.

## <a name="create-a-visualizer-manually"></a>Crear un visualizador manualmente

Siga las tareas siguientes para crear un visualizador.

### <a name="to-create-a-class-library-project"></a>Para crear un proyecto de biblioteca de clases

* Cree un nuevo proyecto de biblioteca de clases.

    ::: moniker range=">=vs-2019"
    Elija **Archivo** > **Nuevo** > **Proyecto**. En la lista desplegable de lenguaje, elija **C#** . En el cuadro de búsqueda, escriba **biblioteca de clases** y, después, elija **Biblioteca de clases (.NET Framework)** . Haga clic en **Next**. En el cuadro de diálogo que aparece, escriba el nombre `MyFirstVisualizer` y, después, haga clic en **Crear**.

    Para el proyecto del visualizador, asegúrese de seleccionar una biblioteca de clases de .NET Framework y no de .NET. Aunque el visualizador debe ser de .NET Framework, la aplicación que realiza la llamada puede ser de .NET Core.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual C#** , elija **.NET Framework** y, luego, en el panel central, **Biblioteca de clases (.NET Framework)** .

    Escriba un nombre adecuado para la biblioteca de clases, como `MyFirstVisualizer` y luego haga clic en **Crear** o **Aceptar**.
    ::: moniker-end

   Después de crear la biblioteca de clases, debe agregar una referencia a Microsoft.VisualStudio.DebuggerVisualizers.DLL, para poder utilizar las clases que allí se definen. No obstante, antes de agregar la referencia, debe cambiar los nombres de algunas clases para que sean significativos.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Para cambiar el nombre de Class1.cs y agregar Microsoft.VisualStudio.DebuggerVisualizers

1. En el **Explorador de soluciones**, haga clic con el botón derecho en Class1.cs y elija **Cambiar nombre** en el menú contextual.

2. Cambie el nombre Class1.cs por un nombre significativo, como DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cambia automáticamente la declaración de clase en DebuggerSide.cs para que coincida con el nuevo nombre del archivo.

3. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y después elija **Agregar referencia** en el menú contextual.

4. En el cuadro de diálogo **Agregar referencia**, en la pestaña **Examinar**, seleccione **Examinar** y busque Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Puede encontrar el archivo DLL en el subdirectorio *\<Visual Studio Install Directory>\Common7\IDE\PublicAssemblies* del directorio de instalación de Visual Studio.

5. Haga clic en **Aceptar**.

6. En DebuggerSide.cs, agregue lo siguiente a las directivas `using`:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Ahora, ya está listo para crear el código del depurador. Éste es el código que se ejecuta dentro del depurador para mostrar la información que desea visualizar. En primer lugar hay que cambiar la declaración del objeto `DebuggerSide` para que herede de la clase base `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Para heredar de DialogDebuggerVisualizer

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
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  El método `Show` contiene el código que verdaderamente crea el cuadro de diálogo del visualizador, u otra interfaz de usuario, y muestra la información que se ha pasado del depurador al visualizador. Es necesario agregar el código que crea el cuadro de diálogo y muestra la información. En este tutorial, se realizará este paso mediante un cuadro de mensaje de formularios Windows Forms. En primer lugar debe agregar una referencia y una directiva `using` para System.Windows.Forms.

### <a name="to-add-systemwindowsforms"></a>Para agregar System.Windows.Forms

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y después elija **Agregar referencia** en el menú contextual.

2. En el cuadro de diálogo **Agregar referencia**, en la pestaña **Examinar**, seleccione **Examinar** y busque System.Windows.Forms.DLL.

    Puede encontrar el archivo DLL en *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Haga clic en **Aceptar**.

4. En DebuggerSide.cs, agregue lo siguiente a las directivas `using`:

   ```csharp
   using System.Windows.Forms;
   ```

   Ahora, agregará código para crear y mostrar la interfaz de usuario para el visualizador. Debido que éste es su primer visualizador, mantendremos la interfaz de usuario sencilla y utilizaremos un cuadro de mensaje.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Para mostrar el resultado del visualizador en un cuadro de diálogo

1. En el método `Show`, agregue la siguiente línea de código:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    En este código de ejemplo no se incluye el control de errores. Debe incluir el control de errores en un visualizador real o en cualquier otro tipo de aplicación.

2. En el menú **Compilar**, elija **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   Ése es el fin del código del depurador. Sin embargo, hay un paso más que realizar; el atributo que indica al lado depurado qué colección de clases incluye el visualizador.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Para agregar el tipo que se va a visualizar en el código del lado depurado

En el código del depurador, especifique el tipo que se va a visualizar (el origen del objeto) en el lado depurado con el atributo <xref:System.Diagnostics.DebuggerVisualizerAttribute>. La propiedad `Target` establece el tipo que se va a visualizar.

1. Agregue el código de atributo siguiente a DebuggerSide.cs, después de las directivas `using`, pero antes de `namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. En el menú **Compilar**, elija **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   En este momento, el primer visualizador está terminado. Si ha seguido los pasos correctamente, debería poder compilar el visualizador e instalarlo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sin embargo, antes de instalar un visualizador en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], debería probarlo para asegurarse de que se ejecuta correctamente. A continuación creará un instrumento de prueba para ejecutar el visualizador sin instalarlo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Para agregar un método de prueba para mostrar el visualizador

1. Agregue el método siguiente a la clase `public DebuggerSide`:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. En el menú **Compilar**, elija **Compilar MyFirstVisualizer**. El proyecto debería compilarse correctamente. Corrija cualquier error de compilación antes de continuar.

   Luego, debe crear un proyecto ejecutable para llamar al archivo DLL del visualizador. Para que resulte más sencillo, use un proyecto de aplicación de consola.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Para agregar un proyecto de aplicación de consola a la solución

1. En el Explorador de soluciones, haga clic con el botón derecho en la solución; luego, elija **Agregar** y haga clic en **Nuevo proyecto**.

    ::: moniker range=">=vs-2019"

    Elija **Archivo** > **Nuevo** > **Proyecto**. En la lista desplegable de lenguaje, elija **C#** . En el cuadro de búsqueda, escriba **consola** y, luego, seleccione **Aplicación de consola (.NET Framework)** o **Aplicación de consola** para .NET. Haga clic en **Next**. En el cuadro de diálogo que aparece, escriba el nombre `MyTestConsole` y, después, haga clic en **Crear**.

    > [!NOTE]
    > Si quiere probar el visualizador mediante una herramienta de ejecución de pruebas, cree una aplicación de consola de .NET Framework. En su lugar, puede crear una aplicación de consola de .NET, pero la herramienta de ejecución de pruebas que se describe más adelante todavía no es compatible con .NET, por lo que tendrá que instalar el visualizador para probarla. En este escenario, cree primero la aplicación de consola y, después, siga los pasos descritos en [Adición de un objeto de datos depurado](#add-a-debuggee-side-data-object).
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual C#** , elija **Escritorio de Windows** y luego, en el panel central, **Aplicación de consola (.NET Framework)** .

    Escriba un nombre adecuado para la biblioteca de clases, como `MyTestConsole` y, después, haga clic en **Aceptar**.
    ::: moniker-end

   Ahora, debe agregar las referencias necesarias para que MyTestConsole pueda llamar a MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Para agregar las referencias necesarias a MyTestConsole

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y elija **Agregar referencia** en el menú contextual.

2. En el cuadro de diálogo **Agregar referencia**, en la ficha **Examinar**, elija Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Haga clic en **Aceptar**.

4. Haga clic con el botón derecho en **MyTestConsole** y elija nuevamente **Agregar referencia**.

5. En el cuadro de diálogo **Agregar referencia**, haga clic en la ficha **Proyectos** y después haga clic en MyFirstVisualizer.

6. Haga clic en **Aceptar**.

   A continuación, agregará el código para finalizar el instrumento de prueba.

### <a name="to-add-code-to-mytestconsole"></a>Para agregar el código a MyTestConsole

1. En el **Explorador de soluciones**, haga clic con el botón derecho en Program.cs y elija **Cambiar nombre** en el menú contextual.

2. Cambie el nombre Program.cs por un nombre más significativo, como TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cambia automáticamente la declaración de clase de TestConsole.cs para que coincida con el nuevo nombre del archivo.

3. En TestConsole.cs, agregue el siguiente código a las directivas `using`:

   ```csharp
   using MyFirstVisualizer;
   ```

4. En el método `Main`, agregue el código siguiente:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Ahora, está listo para probar el primer visualizador.

### <a name="to-test-the-visualizer"></a>Para probar el visualizador

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **MyTestConsole** y, en el menú contextual, elija **Establecer como proyecto de inicio**.

2. En el menú **Depurar**, elija **Iniciar**.

    Se iniciará la aplicación de consola y aparecerá el visualizador, que mostrará la cadena "Hello, World".

   Enhorabuena. Acaba de crear y probar el primer visualizador.

   Si desea utilizar el visualizador en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en lugar de simplemente llamarlo desde el instrumento de prueba, tendrá que instalarlo. Para obtener más información, vea [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md).

::: moniker range=">=vs-2019"
## <a name="add-a-debuggee-side-data-object"></a>Adición de un objeto de datos depurado

En esta sección, se cambia del objeto de datos `System.String` por un objeto de datos personalizado.  

1. Elija **Archivo** > **Nuevo** > **Proyecto**. En la lista desplegable de lenguaje, elija **C#** . En el cuadro de búsqueda, escriba **biblioteca de clases** y, después, elija **Biblioteca de clases (.NET Framework)** o **Biblioteca de clases** para .NET Standard.

   >[!NOTE]
   >Si usa una aplicación de consola de prueba de .NET Framework, asegúrese de crear un proyecto de biblioteca de clases de .NET Framework.

1. Haga clic en **Next**. En el cuadro de diálogo que aparece, escriba el nombre `MyDataObject` y, después, haga clic en **Crear**.

1. (Solo para la biblioteca de clases de .NET Standard) En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Editar archivo de proyecto**. Cambie el valor `<TargetFramework>` por `netstandard2.0`.

1. Dentro del espacio de nombres `MyDataObject`, reemplace el código predeterminado por el siguiente.

   ```csharp
   [Serializable] 
   public class CustomDataObject
   {
      public CustomDataObject()
      {
         this.MyData = "MyTestData";
      }
      public string MyData { get; set; }
   }
   ```

   Para un visualizador de solo lectura, como el de este ejemplo, no es necesario implementar métodos de [VisualizerObjectSource](/dotnet/api/microsoft.visualstudio.debuggervisualizers.visualizerobjectsource).

   A continuación, actualice el proyecto MyFirstVisualizer para usar el nuevo objeto de datos.

1. En el Explorador de soluciones del proyecto MyFirstVisualizer, haga clic con el botón derecho en el nodo **Referencias** y elija **Agregar referencia**.

1. En **Proyectos**, seleccione el proyecto **MyDataObject**.

1. En el código de atributo de DebuggerSide.cs, actualice el valor de Target y cambie `System.String` por `MyDataObject.CustomDataObject`.

   ```csharp
   Target = typeof(MyDataObject.CustomDataObject),
   ```

1. En el proyecto MyFirstVisualizer, reemplace el código del método `Show` por el código siguiente.

   ```csharp
   var data = objectProvider.GetObject() as MyDataObject.CustomDataObject;

   // You can replace displayForm with your own custom Form or Control.  
   Form displayForm = new Form();
   displayForm.Text = data.MyData;
   windowService.ShowDialog(displayForm);
   ```

   En el código anterior se usa una propiedad del objeto de datos para mostrar el título del formulario.

   A continuación, actualice la aplicación de consola para usar el objeto de datos personalizado.

1. En el Explorador de soluciones del proyecto MyTestConsole, haga clic con el botón derecho en el nodo **Referencias**  o **Dependencias** y agregue una referencia de proyecto a `MyDataObject`.

1. En Program.cs, reemplace el código del método `Main` por el código siguiente.

   ```csharp
   // String myString = "Hello, World";
   CustomDataObject customDataObject = new CustomDataObject();

   DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   ```

1. (Aplicación de consola de .NET) Incluya la llamada a `TestShowVisualizer` en una instrucción try-catch, ya que no se admite la herramienta de ejecución de pruebas.

   ```csharp
   try
   {
         DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   }
   catch (Exception) {
   }
   ```

   El depurador necesita una referencia al visualizador. Una manera de mantener la referencia consiste en conservar el código anterior.

1. Para una aplicación de consola de .NET Framework, puede ejecutar la herramienta de ejecución de pruebas (presione **F5**), o bien seguir las instrucciones de [Procedimiento para instalar un visualizador](../debugger/how-to-install-a-visualizer.md).

   Si ejecuta la aplicación mediante la herramienta de ejecución de pruebas, la aplicación muestra el formulario Windows.

1. Para una aplicación de consola de .NET, copie `MyFirstVisualizer.dll` y `MyDataObject.dll` en las carpetas descritas en [Procedimiento para instalar un visualizador](../debugger/how-to-install-a-visualizer.md).

1. Después de instalar el visualizador, establezca un punto de interrupción, ejecute la aplicación de consola y mantenga el puntero sobre `customDataObject`. Si todo se ha configurado correctamente, debería ver el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador").

   :::image type="content" source="../debugger/media/vs-2019/visualizer-csharp-data-object.png" alt-text="Icono de lupa del visualizador.":::

   Al elegir **MyFirstVisualizer** en la lupa, verá el formulario con el texto del objeto de datos en el título.

   ![Formulario de Windows mostrado en el visualizador](../debugger/media/vs-2019/visualizer-csharp-windows-form.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Creación de un visualizador mediante la plantilla de elemento Visualizador

Hasta ahora, en este tutorial se ha mostrado cómo crear manualmente un visualizador. Esto se realizó como un ejercicio de aprendizaje. Ahora que sabe cómo funciona un visualizador sencillo, existe una manera más fácil de crear uno: mediante la plantilla de elementos del visualizador.

En primer lugar, debe crear un nuevo proyecto de biblioteca de clases.

### <a name="to-create-a-new-class-library"></a>Para crear una nueva biblioteca de clases

1. En el menú **Archivo**, elija **Nuevo > Proyecto**.

2. En el cuadro de diálogo **Nuevo proyecto**, en **Visual C#** , seleccione **.NET Framework**.

3. En el panel central, elija **Biblioteca de clases**.

4. En el cuadro **Nombre**, escriba un nombre adecuado para la biblioteca de clases como, por ejemplo, MySecondVisualizer.

5. Haga clic en **Aceptar**.

   A continuación, puede agregarle un elemento del visualizador:

### <a name="to-add-a-visualizer-item"></a>Para agregar un elemento del visualizador

1. En el **Explorador de soluciones**, haga clic con el botón derecho en MySecondVisualizer.

2. En el menú contextual, elija **Agregar** y después haga clic en **Nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento**, en **Elementos de Visual C#** , seleccione **Visualizador del depurador**.

4. En el cuadro **Nombre**, escriba un nombre adecuado, como SecondVisualizer.cs.

5. Haga clic en **Agregar**.

   Eso es todo lo que tiene que hacer. Examine el archivo SecondVisualizer.cs y observe el código que la plantilla ha agregado por usted. Continúe y experimente con el código. Ahora que conoce los fundamentos, ya puede crear visualizadores más complejos y útiles.
::: moniker-end

## <a name="see-also"></a>Vea también

- [Arquitectura de un visualizador](../debugger/visualizer-architecture.md)
- [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
