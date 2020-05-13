---
title: Creación de una página de inicio personalizada ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739633"
---
# <a name="creating-a-custom-start-page"></a>Creación de una página de inicio personalizada

Puede crear una página de inicio personalizada siguiendo los pasos de este documento.

## <a name="create-a-blank-start-page"></a>Crear una página de inicio en blanco

En primer lugar, cree una página de inicio en blanco mediante la creación de un archivo *.xaml* que tenga una estructura de etiquetas que Visual Studio reconocerá. A continuación, agregue marcado y código subyacente para producir la apariencia y la funcionalidad que desee.

1. Cree un nuevo proyecto del tipo **Aplicación WPF** ( Escritorio de**Windows**de Visual**C .** > 

2. Agregue una referencia a `Microsoft.VisualStudio.Shell.14.0`.

3. Abra el archivo XAML en el editor \<XML y cambie \<el elemento de> Window de nivel superior a un elemento de> UserControl sin quitar ninguna de las declaraciones de espacio de nombres.

4. Quite `x:Class` la declaración del elemento de nivel superior. Esto hace que el contenido XAML sea compatible con la ventana de herramientas de Visual Studio que hospeda la página de inicio.

5. Agregue las siguientes declaraciones de \<espacio de nombres al elemento> UserControl de nivel superior.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Estos espacios de nombres le permiten tener acceso a los comandos, controles y configuración de la interfaz de usuario de Visual Studio. Para obtener más información, vea [Agregar comandos](../extensibility/adding-visual-studio-commands-to-a-start-page.md)de Visual Studio a una página de inicio .

     En el ejemplo siguiente se muestra el marcado en el archivo *.xaml* para una página de inicio en blanco. Cualquier contenido personalizado debe <xref:System.Windows.Controls.Grid> ir en el elemento interno.

    ```vb
    <UserControl
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        xmlns:local="clr-namespace:StartPageHost"
        mc:Ignorable="d"
         Height="350" Width="525">
        <Grid>
        <!--Add content here.-->
        </Grid>
    </UserControl>
    ```

6. Agregue controles al \<elemento> UserControl vacío para rellenar la página de inicio personalizada. Para obtener información acerca de cómo agregar funcionalidad específica de Visual Studio, vea [Agregar comandos](../extensibility/adding-visual-studio-commands-to-a-start-page.md)de Visual Studio a una página de inicio .

## <a name="test-and-apply-the-custom-start-page"></a>Pruebe y aplique la página de inicio personalizada

No establezca la instancia principal de Visual Studio para ejecutar la página de inicio personalizada hasta que compruebe que no se bloquea Visual Studio. En su lugar, pruébelo en la instancia experimental.

### <a name="to-test-a-manually-created-custom-start-page"></a>Para probar una página de inicio personalizada creada manualmente

1. Copie el archivo XAML y los archivos de texto o archivos de marcado compatibles en la carpeta *%USERPROFILE%-Mis documentos-Visual Studio 2015-StartPages.\\ *

2. Si la página de inicio hace referencia a los controles o tipos de ensamblados que Visual Studio no instala, copie los ensamblados y, a continuación, péguelos en la *carpeta\\*de instalación de Visual Studio.

3. En un símbolo del sistema de Visual Studio, escriba **devenv /rootsuffix Exp** para abrir una instancia experimental de Visual Studio.

4. En la instancia experimental, vaya a**Environment** >  **la** > página**Inicio** del entorno de**opciones** > de herramientas y seleccione el archivo XAML en el menú desplegable Personalizar página de **inicio.**

5. En el menú **Vista** , haga clic en **Página de inicio**.

     Se debe mostrar la página de inicio personalizada. Si desea cambiar cualquier archivo, debe cerrar la instancia experimental, realizar los cambios, copiar y pegar los archivos modificados y, a continuación, volver a abrir la instancia experimental para ver los cambios.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Para aplicar la página de inicio personalizada en la instancia principal de Visual Studio

- Después de probar la página de inicio y encontrar que es estable, use la opción **Personalizar página** de inicio en el cuadro de diálogo **Opciones** para seleccionarla como la página de inicio en la instancia principal de Visual Studio

## <a name="see-also"></a>Vea también

- [Tutorial: Agregar XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Agregar control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)
- [Agregar comandos de Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Tutorial: Guardar la configuración de usuario en una página de inicio](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Implementar páginas de inicio personalizadas](../extensibility/deploying-custom-start-pages.md)
