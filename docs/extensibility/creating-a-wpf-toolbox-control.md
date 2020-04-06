---
title: Creación de un control de cuadro de herramientas de WPF (WPF Toolbox Control) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739571"
---
# <a name="create-a-wpf-toolbox-control"></a>Crear un control de cuadro de herramientas de WPF

La plantilla Control de cuadro de herramientas de WPF (Windows Presentation Framework) permite crear controles WPF que se agregan automáticamente al cuadro de **herramientas** cuando se instala la extensión. En este tutorial se muestra cómo usar la plantilla para crear un control **de cuadro** de herramientas que puede distribuir a otros usuarios.

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-the-toolbox-control"></a>Crear el control de cuadro de herramientas

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Cree una extensión con un control DE cuadro de herramientas de WPF

1. Cree un proyecto `MyToolboxControl`VSIX denominado . Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".

2. Cuando se abra el proyecto, agregue `MyToolboxControl`una plantilla de elemento Control de cuadro de herramientas de **WPF** denominada . En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a**Extensibilidad** de **Visual C-** > y seleccione Control de cuadro de **herramientas de WPF**. En el campo **Nombre** en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *MyToolboxControl.cs*.

    La solución ahora contiene `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> un control de usuario, un que agrega el control al cuadro de **herramientas**y una entrada **Microsoft.VisualStudio.ToolboxControl** Asset en el manifiesto VSIX para la implementación.

#### <a name="to-create-the-control-ui"></a>Para crear la interfaz de usuario del control

1. Abra *MyToolboxControl.xaml* en el diseñador.

    El diseñador muestra un control <xref:System.Windows.Controls.Grid> que contiene un control <xref:System.Windows.Controls.Button>.

2. Organice el diseño de cuadrícula. Al seleccionar <xref:System.Windows.Controls.Grid> el control, aparecen barras de control azules en los bordes superior e izquierdo de la cuadrícula. Puede agregar filas y columnas a la cuadrícula haciendo clic en las barras.

3. Agregue controles secundarios a la cuadrícula. Puede colocar un control secundario arrastrándolo desde el **cuadro** de herramientas `Grid.Row` `Grid.Column` a una sección de la cuadrícula o estableciendo sus atributos y sus atributos en el XAML. En el ejemplo siguiente se agregan dos etiquetas en la fila superior de la cuadrícula y un botón en la segunda fila.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Cambiar el nombre del control

 De forma predeterminada, el control aparecerá en el cuadro de **herramientas** como **MyToolboxControl** en un grupo denominado **MyToolboxControl.MyToolboxControl**. Puede cambiar estos nombres en el archivo *MyToolboxControl.xaml.cs.*

1. Abra *MyToolboxControl.xaml.cs* en la vista de código.

2. Busque `MyToolboxControl` la clase y cámbiele el nombre a TestControl. (La forma más rápida de hacerlo es cambiar el nombre de la clase, luego seleccione **Cambiar nombre** en el menú contextual y completar los pasos. (Para obtener más información acerca del comando **Cambiar nombre,** vea Cambiar el nombre de [la refactorización (C-)](../ide/reference/rename.md).)

3. Vaya al `ProvideToolboxControl` atributo y cambie el valor del primer parámetro a **Test**. Este es el nombre del grupo que contendrá el control en el cuadro de **herramientas**.

    El código resultante debería tener este aspecto:

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

 Al depurar el proyecto, debe encontrar el control instalado en el cuadro de **herramientas** de la instancia experimental de Visual Studio.

### <a name="to-build-and-test-the-control"></a>Para compilar y probar el control

1. Vuelva a generar el proyecto e inicie la depuración.

2. En la nueva instancia de Visual Studio, cree un proyecto de aplicación WPF. Asegúrate de que el Diseñador XAML está abierto.

3. Busque el control en el **Cuadro de herramientas** y arrástrelo a la superficie de diseño.

4. Inicie la depuración de la aplicación WPFWPF.

5. Compruebe que aparece el control.

### <a name="to-deploy-the-control"></a>Para implementar el control

1. Después de compilar el proyecto probado, puede encontrar el archivo *.vsix* en la carpeta *-bin-debug\* del proyecto.

2. Puede instalarlo en un equipo local haciendo doble clic en el archivo *.vsix* y siguiendo el procedimiento de instalación. Para desinstalar el control, vaya **a** > **Extensiones de** herramientas y actualizaciones y busque la extensión de control y, a continuación, haga clic en **Desinstalar**.

3. Cargue el archivo *.vsix* en una red o en un sitio Web.

    Si carga el archivo en el sitio Web de [Visual Studio Marketplace,](https://marketplace.visualstudio.com/) otros usuarios pueden usar **extensiones** > **y actualizaciones** de herramientas en Visual Studio para buscar el control en línea e instalarlo.
