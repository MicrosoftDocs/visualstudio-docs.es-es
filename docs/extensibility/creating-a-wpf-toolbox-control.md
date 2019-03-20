---
title: Crear un Control de cuadro de herramientas WPF | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 811c87f73d1122b3e97ffdef9b4d3f6c044ce941
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194832"
---
# <a name="create-a-wpf-toolbox-control"></a>Crear un Control de cuadro de herramientas WPF

La plantilla de Control de cuadro de herramientas WPF (Windows Presentation Framework) le permite crear controles de WPF que se agregan automáticamente a la **cuadro de herramientas** cuando se instala la extensión. En este tutorial se muestra cómo usar la plantilla para crear un **cuadro de herramientas** control que se puede distribuir a otros usuarios.

A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Crear el Control de cuadro de herramientas

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Crear una extensión con un Control de cuadro de herramientas de WPF

1. Cree un proyecto VSIX denominado `MyToolboxControl`. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** diálogo buscando "vsix".

2. Cuando se abra el proyecto, agregue un **Control Toolbox de WPF** plantilla de elemento denominado `MyToolboxControl`. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **agregar** > **nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C#** > **extensibilidad** y seleccione **Control Toolbox de WPF**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para *MyToolboxControl.cs*.

    La solución contiene ahora un control de usuario, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> que agrega el control a la **cuadro de herramientas**y un **Microsoft.VisualStudio.ToolboxControl** entrada del activo en el manifiesto VSIX para  implementación.

#### <a name="to-create-the-control-ui"></a>Para crear la interfaz de usuario del control

1. Abra *MyToolboxControl.xaml* en el diseñador.

    El diseñador muestra un control <xref:System.Windows.Controls.Grid> que contiene un control <xref:System.Windows.Controls.Button>.

2. Organice el diseño de cuadrícula. Cuando se selecciona el <xref:System.Windows.Controls.Grid> controlar, aparecen barras de control en azul en los bordes superiores e izquierdos de la cuadrícula. Puede agregar filas y columnas a la cuadrícula, haga clic en las barras.

3. Agregar controles secundarios a la cuadrícula. Puede colocar un control secundario arrastrándolo desde la **cuadro de herramientas** a una sección de la cuadrícula, o estableciendo su `Grid.Row` y `Grid.Column` atributos en el XAML. El ejemplo siguiente agrega dos etiquetas en la fila superior de la cuadrícula y un botón en la segunda fila.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Cambiar el nombre del control

 De forma predeterminada, el control aparecerá en el **cuadro de herramientas** como **MyToolboxControl** en un grupo denominado **MyToolboxControl.MyToolboxControl**. Puede cambiar estos nombres en el *MyToolboxControl.xaml.cs* archivo.

1. Abra *MyToolboxControl.xaml.cs* en la vista código.

2. Buscar el `MyToolboxControl` clase y cámbielo por TestControl. (La forma más rápida de hacerlo es cambiar el nombre de la clase, a continuación, seleccione **cambiar el nombre** en el menú contextual y complete los pasos. (Para obtener más información sobre la **cambiar el nombre de** de comandos, consulte [cambiar el nombre de refactorización (C#)](../ide/reference/rename.md).)

3. Vaya a la `ProvideToolboxControl` atributo y cambie el valor del primer parámetro a **prueba**. Este es el nombre del grupo que contiene el control en el **cuadro de herramientas**.

    El código resultante debe tener este aspecto:

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>Compilación, prueba e implementación

 Cuando se depura el proyecto, debe buscar el control instalado en el **cuadro de herramientas** de la instancia experimental de Visual Studio.

### <a name="to-build-and-test-the-control"></a>Para compilar y probar el control

1. Recompilar el proyecto e iniciar la depuración.

2. En la nueva instancia de Visual Studio, cree un proyecto de aplicación WPF. Asegúrese de que el Diseñador XAML está abierto.

3. Busque el control en el **Cuadro de herramientas** y arrástrelo a la superficie de diseño.

4. Empiece a depurar la aplicación de WPF.

5. Compruebe que aparece el control.

### <a name="to-deploy-the-control"></a>Para implementar el control

1. Después de compilar el proyecto probado, puede encontrar el *.vsix* de archivos en el * \bin\debug\* carpeta del proyecto.

2. Puede instalar en un equipo local haciendo doble clic en el *.vsix* archivo y siga el procedimiento de instalación. Para desinstalar el control, vaya a **herramientas** > **extensiones y actualizaciones** y busque la extensión de control, a continuación, haga clic en **desinstalar**.

3. Cargar el *.vsix* archivo a una red o a un sitio Web.

    Si va a cargar el archivo a la [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sitio Web, otros usuarios pueden usar **herramientas** > **extensiones y actualizaciones** en Visual Studio para buscar el controlar en línea e instálelo.
