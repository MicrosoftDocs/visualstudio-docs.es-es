---
title: Ampliación de la barra de estado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 499e6c2b34fcc5261ab8fb3a87a24e2cc0959d8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113747"
---
# <a name="extend-the-status-bar"></a>Ampliar la barra de estado
Puede usar la barra de estado de Visual Studio en la parte inferior del IDE para mostrar información.

 Cuando se amplía la barra de estado, puede mostrar información y la interfaz de usuario en cuatro regiones: la región de comentarios, la barra de progreso, la región de animación y la región del diseñador. La región de comentarios permite mostrar texto y resalte el texto mostrado. La barra de progreso muestra el progreso incremental para realizar operaciones de ejecución breve como guardar un archivo. La región de animación muestra una animación de un bucle continuo para el funcionamiento de longitud indeterminado, como compilar varios proyectos en una solución o las operaciones de larga ejecución. Y la región del diseñador muestra el número de línea y columna de la ubicación del cursor.

 Puede obtener la barra de estado mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interfaz (desde el <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> service). Además, puede registrar cualquier objeto que se encuentra en un marco de ventana como un objeto de cliente de la barra de estado implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interfaz. Cada vez que una ventana se activa, Visual Studio consulta el objeto situado en esa ventana para el `IVsStatusbarUser` interfaz. Si se encuentra, invoca el <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método en la interfaz devuelta y el objeto puede actualizar la barra de estado desde dentro de ese método. Documento windows, por ejemplo, puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método para actualizar la información en la región del diseñador cuando se activan.

 Los procedimientos siguientes se suponen que sabe cómo crear un proyecto de VSIX y agregar un comando de menú personalizado. Para obtener información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modificar la barra de estado
 Este procedimiento muestra cómo establecer y obtener el texto, mostrar texto estático y resalte el texto mostrado en la región de comentarios de la barra de estado.

### <a name="read-and-write-to-the-status-bar"></a>Leer y escribir en la barra de estado

1. Cree un proyecto VSIX denominado **TestStatusBarExtension** y agregue un comando de menú llamado **TestStatusBarCommand**.

2. En *TestStatusBarCommand.cs*, reemplace el código del método de controlador de comandos (`MenuItemCallback`) por lo siguiente:

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

3. Compile el código e iniciar la depuración.

4. Abra el **herramientas** menú en la instancia experimental de Visual Studio. Haga clic en el **TestStatusBarCommand invocar** botón.

     Debería ver que el texto en el estado de la barra ahora lecturas **nos acaba de escribir en la barra de estado.** y el cuadro de mensaje que aparece tiene el mismo texto.

### <a name="update-the-progress-bar"></a>Actualización de la barra de progreso

1. En este procedimiento, se mostrará cómo inicializar y actualizar la barra de progreso.

2. Abra el *TestStatusBarCommand.cs* de archivo y reemplace el `MenuItemCallback` método con el código siguiente:

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

3. Compile el código e iniciar la depuración.

4. Abra el **herramientas** menú en la instancia experimental de Visual Studio. Haga clic en **TestStatusBarCommand invocar** botón.

     Debería ver que el texto en el estado de la barra ahora lecturas **escribir en la barra de progreso.** También debería ver la barra de progreso se actualiza cada segundo durante 20 segundos. Después de que se borran la barra de estado y la barra de progreso.

### <a name="display-an-animation"></a>Mostrar una animación

1. La barra de estado muestra una animación de bucle que indica una operación de larga ejecución (por ejemplo, al compilar varios proyectos en una solución). Si no ve esta animación, asegúrese de que tiene el valor correcto **herramientas** > **opciones** configuración:

     Vaya a la **herramientas** > **opciones** > **General** pestaña y desactive la opción **ajustar automáticamente la experiencia visual según el cliente rendimiento**. A continuación, compruebe las subopciones **habilitar experiencia visual mejorada del cliente**. Ahora podrá ver la animación al compilar el proyecto en la instancia experimental de Visual Studio.

     En este procedimiento se muestra la animación de Visual Studio estándar que representa la creación de un proyecto o solución.

2. Abra el *TestStatusBarCommand.cs* de archivo y reemplace el `MenuItemCallback` método con el código siguiente:

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

3. Compile el código e iniciar la depuración.

4. Abra el **herramientas** menú en la instancia experimental de Visual Studio y haga clic en **TestStatusBarCommand invocar**.

     Cuando aparezca el cuadro de mensaje, también debería ver la animación en la barra de estado de la derecha. Al descartar el cuadro de mensaje, desaparece la animación.