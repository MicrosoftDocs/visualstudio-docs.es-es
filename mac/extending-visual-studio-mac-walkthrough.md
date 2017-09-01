---
title: 'Tutorial: Extender Visual Studio para Mac'
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 7d267051abbf0341b3842b24906e10e0906a0a72
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---

# <a name="extending-visual-studio-for-mac-walkthrough"></a>Tutorial: Extender Visual Studio para Mac

Este tema le guía a lo largo del proceso de creación de [un paquete de extensión sencillo](https://github.com/mjh4/AddIns/tree/master/DateInserter). El paquete de extensión crea un nuevo comando en el menú de edición de Visual Studio para Mac que permite al usuario insertar la fecha y la hora actuales en un documento de texto abierto.

En este ejemplo se usa el complemento Add-in Maker. Add-in Maker crea una nueva plantilla de proyecto y la rellena con los archivos necesarios para el paquete de extensión personalizado.

1.   Comience por iniciar Visual Studio para Mac si aún no está abierto:

  ![Captura de pantalla de Visual Studio para Mac](media/extending-visual-studio-mac-addin3.png)

2.   Instale el _paquete de extensión Add-in Maker_ mediante el Administrador de extensiones. En el menú de Visual Studio, elija **Extensiones...**:

  ![Pestaña Administrador de complementos](media/extending-visual-studio-mac-addin4.png)

3.   Vaya a la pestaña Galería y escriba `Addin Maker` en la barra de búsqueda superior derecha. Seleccione Addin Maker en la categoría de desarrollo de complementos y haga clic en <kbd>Instalar</kbd>. Si no aparece nada, haga clic en Actualizar y busque de nuevo:

  ![Administrador de complementos](media/extending-visual-studio-mac-addin5.png)

4.   Ahora que Addin Maker está instalado, puede empezar a crear un paquete de extensión. Empiece por crear una nueva solución.

5.  En el cuadro de diálogo **Nueva solución**, elija la plantilla **Otros > Varios > General > Xamarin Studio Addin > C#** y en la siguiente pantalla ponga el nombre `DateInserter` a la nueva solución:

  ![Creación de una nueva solución](media/extending-visual-studio-mac-addin7New.png)

6.   Visual Studio para Mac rellena una nueva solución:

  ![Solución rellena](media/extending-visual-studio-mac-addin8.png)

7.   Quite el código de plantilla de `Manifest.addin.xml` y sustitúyalo por lo siguiente:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
        <ExtensionModel>
            <Extension path = "/MonoDevelop/Ide/Commands/Edit">
                <Command id = "DateInserter.DateInserterCommands.InsertDate"
                    _label = "Insert Date"
                    defaultHandler = "DateInserter.InsertDateHandler" />
            </Extension>

            <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
                <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
            </Extension>
        </ExtensionModel>
    ```

8.   Ahora debe configurar los archivos que van a controlar la inserción de la fecha y la hora en el editor de texto. Haga clic con el botón derecho en el nodo del proyecto y agregue un nuevo archivo. Seleccione **General > Clase vacía** y asigne el nombre *InsertDateHandler* al nuevo archivo:

  ![InsertDateHandler](media/extending-visual-studio-mac-addin9.png)

9.   Quite el código de plantilla de `InsertDateHandler.cs` y sustitúyalo por el siguiente código:

    ```cs
    using MonoDevelop.Components.Commands;
    using MonoDevelop.Ide;
    using MonoDevelop.Ide.Gui;
    using System;

    namespace DateInserter
    {
        class InsertDateHandler : CommandHandler
        {
            protected override void Run()
            {

            }

            protected override void Update(CommandInfo info)
            {

            }
        }
    }
    ```

  Estos dos métodos de marcador de posición se expandirán más adelante.

10.   Haga clic con el botón derecho en el proyecto **DateInserter** y seleccione **Agregar > Nuevo archivo**. Seleccione **General > Enumeración vacía** y luego asigne al nuevo archivo el nombre *DateInserterCommands*:

  ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11.   Agregue el comando `InsertDate` como una nueva enumeración al archivo `DateInserterCommands.cs`:

    ``` cs
    using System;

    namespace DateInserter
    {
        public enum DateInserterCommands
        {
            InsertDate,
        }
    }
    ```

12.   En este punto, debe tener un paquete de extensión que funciona. Puede probarlo si guarda el trabajo y ejecuta la aplicación. El IDE iniciará una nueva instancia de Visual Studio para Mac con el nuevo paquete de extensión instalado. Si va al **menú de edición**, verá que Visual Studio para Mac tiene una opción nueva denominada **Insertar fecha**, como se muestra en la captura de pantalla siguiente:

  ![Comando Insertar fecha](media/extending-visual-studio-mac-addin11.png)

  Tenga en cuenta que la selección de Insertar fecha en el menú no tiene ningún efecto porque la implementación actual solo tiene métodos de marcador de posición.

13.   El marco de trabajo está listo para el paquete de extensión, así que es hora de escribir el código que permite insertar la fecha. En primer lugar, asegúrese de que el comando **Insertar fecha** solo esté habilitado cuando el usuario tenga un archivo de texto abierto al reemplazar el método `Update` de `InsertDateHandler.cs` por el código siguiente:

    ```cs
    protected override void Update(CommandInfo info)
    {
        info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14.   Actualice el método `Run` del comando para insertar la fecha y la hora con el código siguiente:

    ``` cs
    protected override void Run () {
        var editor = IdeApp.Workbench.ActiveDocument.Editor;
        var date = DateTime.Now.ToString ();
        editor.InsertAtCaret (date);

    }
    ```

15.   Por último, ejecute el paquete de extensión para probarlo. En la nueva instancia de Visual Studio para Mac, seleccione **Editar > Insertar fecha**. La fecha y la hora actuales se insertan en el símbolo de intercalación, como se muestra en la captura de pantalla siguiente:

  ![Captura de pantalla de Insertar fecha](media/extending-visual-studio-mac-addin12.png)

