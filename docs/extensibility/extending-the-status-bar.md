---
title: Ampliación de la barra de estado de la barra de estado de la barra de estado Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711536"
---
# <a name="extend-the-status-bar"></a>Ampliar la barra de estado
Puede usar la barra de estado de Visual Studio en la parte inferior del IDE para mostrar información.

 Al ampliar la barra de estado, puede mostrar información e interfaz de usuario en cuatro regiones: la región de comentarios, la barra de progreso, la región de animación y la región del diseñador. La región de comentarios le permite mostrar texto y resaltar el texto mostrado. La barra de progreso muestra el progreso incremental de las operaciones de ejecución corta, como guardar un archivo. La región de animación muestra una animación en bucle continuo para operaciones de ejecución prolongada u operación de longitud indeterminada, como la creación de varios proyectos en una solución. Y la región del diseñador muestra el número de línea y columna de la ubicación del cursor.

 Puede obtener la barra de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> estado mediante <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> la interfaz (desde el servicio). Además, cualquier objeto situado en un marco de ventana puede <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> registrarse como un objeto de cliente de barra de estado mediante la implementación de la interfaz. Cada vez que se activa una ventana, Visual Studio `IVsStatusbarUser` consulta el objeto incrustado en esa ventana para la interfaz. Si se encuentra, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> llama al método en la interfaz devuelta y el objeto puede actualizar la barra de estado desde dentro de ese método. Las ventanas de documento, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> por ejemplo, pueden usar el método para actualizar la información de la región del diseñador cuando se activan.

 En los procedimientos siguientes se supone que entiende cómo crear un proyecto VSIX y agregar un comando de menú personalizado. Para obtener información, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modificar la barra de estado
 Este procedimiento muestra cómo establecer y obtener texto, mostrar texto estático y resaltar el texto mostrado en la región de comentarios de la barra de estado.

### <a name="read-and-write-to-the-status-bar"></a>Leer y escribir en la barra de estado

1. Cree un proyecto VSIX denominado **TestStatusBarExtension** y agregue un comando de menú denominado **TestStatusBarCommand**.

2. En *TestStatusBarCommand.cs*, reemplace el`MenuItemCallback`código del método del controlador de comandos ( ) por lo siguiente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Compile el código e inicie la depuración.

4. Abra el menú **Herramientas** en la instancia experimental de Visual Studio. Haga clic en el botón **Invocar TestStatusBarCommand.**

     Debería ver que el texto en la barra de estado ahora dice Acabamos de escribir en la barra de **estado.** y el cuadro de mensaje que aparece tiene el mismo texto.

### <a name="update-the-progress-bar"></a>Actualizar la barra de progreso

1. En este procedimiento vamos a mostrar cómo inicializar y actualizar la barra de progreso.

2. Abra *TestStatusBarCommand.cs* el archivo TestStatusBarCommand.cs `MenuItemCallback` y reemplace el método por el código siguiente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Compile el código e inicie la depuración.

4. Abra el menú **Herramientas** en la instancia experimental de Visual Studio. Haga clic en el botón **Invocar TestStatusBarCommand.**

     Debería ver que el texto de la barra de estado ahora lee Escritura en la barra de **progreso.** También debería ver que la barra de progreso se actualiza cada segundo durante 20 segundos. Después de eso, se borran la barra de estado y la barra de progreso.

### <a name="display-an-animation"></a>Mostrar una animación

1. La barra de estado muestra una animación de bucle que indica una operación de ejecución prolongada (por ejemplo, la creación de varios proyectos en una solución). Si no ve esta animación, asegúrese **Tools** > de que tiene la configuración correcta de**Opciones** de herramientas:

     Vaya a la**pestaña** **Opciones** > generales de **herramientas** > y desactive Ajustar automáticamente la **experiencia visual en función del rendimiento del cliente.** A continuación, compruebe la subopción **Habilitar experiencia visual**de cliente enriquecido . Ahora debería poder ver la animación al compilar el proyecto en la instancia experimental de Visual Studio.

     En este procedimiento se muestra la animación estándar de Visual Studio que representa la creación de un proyecto o solución.

2. Abra *TestStatusBarCommand.cs* el archivo TestStatusBarCommand.cs `MenuItemCallback` y reemplace el método por el código siguiente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Compile el código e inicie la depuración.

4. Abra el menú **Herramientas** en la instancia experimental de Visual Studio y haga clic en **Invocar TestStatusBarCommand**.

     Cuando vea el cuadro de mensaje, también debería ver la animación en la barra de estado en el extremo derecho. Cuando se descarta el cuadro de mensaje, la animación desaparece.
