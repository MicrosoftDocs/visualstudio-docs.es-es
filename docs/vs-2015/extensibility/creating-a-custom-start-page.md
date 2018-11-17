---
title: Creación de un archivo de página de inicio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87f653a6ac745253ae86eb6bf8dfab92169ac4db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806066"
---
# <a name="creating-a-custom-start-page"></a>Creación de una página de inicio personalizada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si no se puede crear una página de inicio personalizada mediante el uso de la plantilla de proyecto de la página de inicio, como se describe en [las páginas de inicio](../misc/creating-your-own-start-page.md), puede crearla manualmente siguiendo los pasos descritos en este documento.  
  
## <a name="creating-a-blank-start-page"></a>Crear una página de inicio en blanco  
 En primer lugar, asegúrese de una página de inicio en blanco mediante la creación de un archivo .xaml que tiene una estructura de la etiqueta a la que Visual Studio reconocerá. A continuación, agregue el marcado y código subyacente para generar el aspecto y funcionalidad que desee.  
  
#### <a name="to-create-a-blank-start-page"></a>Para crear una página de inicio en blanco  
  
1.  Cree un nuevo proyecto del tipo **aplicación WPF** (**Visual C# / Windows Desktop**.  
  
2.  Agregue una referencia a `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Abra el archivo XAML en el editor XML y cambiar el nivel superior \<Ventana > elemento para un \<UserControl > elemento sin quitar cualquiera de las declaraciones de espacio de nombres.  
  
4.  Quitar el `x:Class` declaración de elemento de nivel superior. Esto hace que el contenido XAML que sea compatible con la ventana de herramientas de Visual Studio que hospeda la página de inicio.  
  
5.  Agregue las siguientes declaraciones de espacio de nombres a la observación inicial \<UserControl > elemento.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Estos espacios de nombres le permiten tener acceso a comandos de Visual Studio, los controles y la configuración de la interfaz de usuario. Para obtener más información, consulte [agregar comandos de Microsoft Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     El ejemplo siguiente muestra el marcado en el archivo .xaml para una página de inicio en blanco. Cualquier contenido personalizado debe ir en interno <xref:System.Windows.Controls.Grid> elemento.  
  
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
  
6.  Agregar controles a vacío \<UserControl > elemento para rellenar la página de inicio personalizada. Para obtener información acerca de cómo agregar la funcionalidad que es específica de Visual Studio, consulte [agregar comandos de Microsoft Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Probar y aplicar la página de inicio personalizada  
 No establezca la instancia principal de Visual Studio para ejecutar la página de inicio personalizada hasta que compruebe que no se bloquea Visual Studio. Pruébelo en su lugar, en la instancia experimental.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Para probar una página de inicio personalizada creada manualmente  
  
1.  Copie el archivo XAML y los archivos de texto o marcado auxiliares archivos, a la **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  carpeta.  
  
2.  Si hace referencia a la página de inicio de los tipos en ensamblados que no se instalan con Visual Studio o los controles, copie los ensamblados y, a continuación, péguelos en _carpeta de instalación de Visual Studio_**\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  En un símbolo del sistema de Visual Studio, escriba **devenv /rootsuffix Exp** para abrir una instancia experimental de Visual Studio.  
  
4.  En la instancia experimental, vaya a la **herramientas / opciones / entorno / inicio** página y seleccione el archivo XAML desde el **Personalizar página principal** lista desplegable.  
  
5.  En el menú **Vista** , haga clic en **Página de inicio**.  
  
     Debe mostrarse la página de inicio personalizada. Si desea cambiar todos los archivos, debe cerrar la instancia experimental, realice los cambios, copie y pegue los archivos modificados y, a continuación, vuelva a abrir la instancia experimental para ver los cambios.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Para aplicar personalizado página de inicio en la instancia principal de Visual Studio  
  
-   Después de haber probado su página de inicio y ha determinado que es estable, utilice el **Personalizar página principal** opción el **opciones** cuadro de diálogo para seleccionarla como la página de inicio en la instancia principal de Visual Studio  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Agregar XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Agregar Control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)   
 [Adición de comandos de Visual Studio a una página de inicio](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Tutorial: Guardar configuración de usuario en una página de inicio](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Implementación de páginas de inicio personalizadas](../extensibility/deploying-custom-start-pages.md)

