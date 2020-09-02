---
title: Crear una página de inicio personalizada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acb7922658a5dd7db0839051a42a119733c8b1d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184202"
---
# <a name="creating-a-custom-start-page"></a>Creación de una página de inicio personalizada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si no puede crear una página de inicio personalizada con la plantilla de proyecto de página de inicio, tal y como se describe en [páginas de inicio](../misc/creating-your-own-start-page.md), puede crear manualmente una siguiendo los pasos descritos en este documento.  
  
## <a name="creating-a-blank-start-page"></a>Crear una página de inicio en blanco  
 En primer lugar, cree una página de inicio en blanco mediante la creación de un archivo. XAML que tenga una estructura de etiqueta que Visual Studio reconozca. A continuación, agregue marcado y código subyacente para generar la apariencia y la funcionalidad que desee.  
  
#### <a name="to-create-a-blank-start-page"></a>Para crear una página de inicio en blanco  
  
1. Cree un nuevo proyecto del tipo **aplicación WPF** (**Visual C#/escritorio de Windows**).  
  
2. Agregue una referencia a `Microsoft.VisualStudio.Shell.14.0`.  
  
3. Abra el archivo XAML en el editor XML y cambie el elemento de nivel superior \<Window> a un \<UserControl> elemento sin quitar las declaraciones de espacio de nombres.  
  
4. Quite la `x:Class` declaración del elemento de nivel superior. Esto hace que el contenido XAML sea compatible con la ventana de herramientas de Visual Studio que hospeda la página de inicio.  
  
5. Agregue las siguientes declaraciones de espacio de nombres al elemento de nivel superior \<UserControl> .  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Estos espacios de nombres permiten tener acceso a los comandos, controles y configuración de la interfaz de usuario de Visual Studio. Para obtener más información, vea [Agregar comandos de Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     En el ejemplo siguiente se muestra el marcado en el archivo. XAML para una página de inicio en blanco. Cualquier contenido personalizado debe ir en el <xref:System.Windows.Controls.Grid> elemento interno.  
  
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
  
6. Agregue controles al elemento vacío \<UserControl> para rellenar la página de inicio personalizada. Para obtener información sobre cómo agregar funcionalidad específica de Visual Studio, vea [Agregar comandos de Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Probar y aplicar la página de inicio personalizada  
 No establezca la instancia principal de Visual Studio para ejecutar la página de inicio personalizada hasta que compruebe que no se bloquea en Visual Studio. En su lugar, pruébelo en la instancia experimental.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Para probar una página de inicio personalizada creada manualmente  
  
1. Copie el archivo XAML, y los archivos de texto o de marcado auxiliares, en la carpeta **%userprofile%\My Documentos\visual Studio 2015 \\ \ StartPages** .  
  
2. Si la página de inicio hace referencia a los controles o tipos de los ensamblados que no se instalan con Visual Studio, copie los ensamblados y péguelos en la _carpeta de instalación de Visual Studio_** \\ \Common7\IDE\PrivateAssemblies**.  
  
3. En un símbolo del sistema de Visual Studio, escriba **devenv/Rootsuffix exp** para abrir una instancia experimental de Visual Studio.  
  
4. En la instancia experimental, vaya a la página **herramientas/opciones/entorno/Inicio** y seleccione el archivo XAML en el menú desplegable **Personalizar Página de inicio** .  
  
5. En el menú **Vista** , haga clic en **Página de inicio**.  
  
     Se debe mostrar la página de inicio personalizada. Si desea cambiar cualquier archivo, debe cerrar la instancia experimental, realizar los cambios, copiar y pegar los archivos modificados y, a continuación, volver a abrir la instancia experimental para ver los cambios.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Para aplicar la página de inicio personalizada en la instancia principal de Visual Studio  
  
- Después de probar la página de inicio y de que se encuentre estable, use la opción **personalizar la página de inicio** del cuadro de diálogo **Opciones** para seleccionarla como página de inicio en la instancia principal de Visual Studio.  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial: agregar XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Agregar el control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)   
 [Agregar comandos de Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Tutorial: guardar la configuración de usuario en una página de inicio](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Implementación de páginas de inicio personalizadas](../extensibility/deploying-custom-start-pages.md)
