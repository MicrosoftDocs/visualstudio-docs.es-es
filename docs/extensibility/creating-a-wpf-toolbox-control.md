---
title: Crear un control de cuadro de herramientas de WPF | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
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
ms.openlocfilehash: a6aa6051648e495e21f7954a737f7b572ce6a6f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903946"
---
# <a name="create-a-wpf-toolbox-control"></a>Crear un control de cuadro de herramientas de WPF

La plantilla control Toolbox de WPF (Windows Presentation Framework) le permite crear controles de WPF que se agregan automáticamente al **cuadro de herramientas** cuando se instala la extensión. En este tutorial se muestra cómo usar la plantilla para crear un control de **cuadro de herramientas** que se puede distribuir a otros usuarios.

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Crear el control Toolbox

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Crear una extensión con un control de cuadro de herramientas de WPF

1. Cree un proyecto VSIX denominado `MyToolboxControl` . Para buscar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , busque "VSIX".

2. Cuando se abra el proyecto, agregue una plantilla de elemento de **control de cuadro de herramientas de WPF** denominada `MyToolboxControl` . En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a extensibilidad de **Visual C#**  >  **Extensibility** y seleccione **control de cuadro de herramientas de WPF**. En el campo **nombre** situado en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *MyToolboxControl.CS*.

    La solución contiene ahora un control de usuario, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> que agrega el control al **cuadro de herramientas**y una entrada de recurso **Microsoft. VisualStudio. TOOLBOXCONTROL** en el manifiesto de VSIX para la implementación.

#### <a name="to-create-the-control-ui"></a>Para crear la interfaz de usuario del control

1. Abra *MyToolboxControl. Xaml* en el diseñador.

    El diseñador muestra un control <xref:System.Windows.Controls.Grid> que contiene un control <xref:System.Windows.Controls.Button>.

2. Organice el diseño de la cuadrícula. Al seleccionar el <xref:System.Windows.Controls.Grid> control, aparecen barras de control azules en los bordes superior e izquierdo de la cuadrícula. Puede Agregar filas y columnas a la cuadrícula haciendo clic en las barras.

3. Agregar controles secundarios a la cuadrícula. Puede colocar un control secundario arrastrándolo desde el **cuadro de herramientas** a una sección de la cuadrícula, o estableciendo sus `Grid.Row` `Grid.Column` atributos y en el código XAML. En el ejemplo siguiente se agregan dos etiquetas en la fila superior de la cuadrícula y un botón en la segunda fila.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Cambiar el nombre del control

 De forma predeterminada, el control aparecerá en el **cuadro de herramientas** como **MyToolboxControl** en un grupo llamado **MyToolboxControl. MyToolboxControl**. Puede cambiar estos nombres en el archivo *MyToolboxControl.Xaml.CS* .

1. Abra *MyToolboxControl.Xaml.CS* en la vista de código.

2. Busque la `MyToolboxControl` clase y cambie su nombre a TestControl. (La forma más rápida de hacerlo es cambiar el nombre de la clase y, a continuación, seleccionar **cambiar nombre** en el menú contextual y completar los pasos. (Para obtener más información sobre el comando **Rename** , vea [refactorización de cambio de nombre (C#)](../ide/reference/rename.md)).

3. Vaya al `ProvideToolboxControl` atributo y cambie el valor del primer parámetro a **Test**. Este es el nombre del grupo que contendrá el control en el **cuadro de herramientas**.

    El código resultante debe ser similar al siguiente:

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

## <a name="build-test-and-deployment"></a>Compilación, pruebas e implementación

 Al depurar el proyecto, debe buscar el control instalado en el **cuadro de herramientas** de la instancia experimental de Visual Studio.

### <a name="to-build-and-test-the-control"></a>Para compilar y probar el control

1. Vuelva a compilar el proyecto e iniciar la depuración.

2. En la nueva instancia de Visual Studio, cree un proyecto de aplicación WPF. Asegúrese de que el Diseñador XAML está abierto.

3. Busque el control en el **Cuadro de herramientas** y arrástrelo a la superficie de diseño.

4. Iniciar la depuración de la aplicación WPF.

5. Compruebe que aparece el control.

### <a name="to-deploy-the-control"></a>Para implementar el control

1. Después de compilar el proyecto probado, puede encontrar el archivo *. vsix* en la carpeta * \bin\debug \* del proyecto.

2. Para instalarlo en un equipo local, haga doble clic en el archivo *. vsix* y siga el procedimiento de instalación. Para desinstalar el control, vaya a **herramientas**  >  **extensiones y actualizaciones** , busque la extensión de control y haga clic en **desinstalar**.

3. Cargue el archivo *. vsix* en una red o en un sitio Web.

    Si carga el archivo en el sitio web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , otros usuarios pueden usar las extensiones de **herramientas**  >  **y las actualizaciones** en Visual Studio para buscar el control en línea e instalarlo.
