---
title: Ampliación del Shell aislado | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc700e0a1b8753a26067eff90df9ff58765de8d1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792026"
---
# <a name="extending-the-isolated-shell"></a>Ampliación del Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender el shell aislado de Visual Studio mediante la adición de un VSPackage, una parte del componente de Managed Extensibility Framework (MEF) o un proyecto VSIX genérico a la aplicación de shell aislado.  
  
> [!NOTE]
>  Los pasos siguientes implican que ha creado una aplicación básica de shell aislado mediante el uso de la plantilla de proyecto de Visual Studio Shell aislado. Para obtener más información acerca de esta plantilla de proyecto, vea [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Ubicaciones de las plantillas de proyecto del paquete de Visual Studio  
 La plantilla de proyecto del paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes en el cuadro de diálogo **Nuevo proyecto** :  
  
1.  En **Visual Basic**, **extensibilidad**. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2.  En **Visual C#**, **extensibilidad**. El lenguaje predeterminado del proyecto es C#.  
  
3.  En **otros tipos de proyecto**, **extensibilidad**. El lenguaje predeterminado del proyecto es C++.  
  
## <a name="adding-a-vspackage"></a>Adición de un VSPackage  
 Un VSPackage puede agregar a la aplicación de shell aislado. Los pasos siguientes muestran cómo crear uno que agregue los comandos de menú.  
  
#### <a name="to-add-a-new-vspackage"></a>Para agregar un nuevo paquete de VS  
  
1.  Agregue un proyecto de paquete de Visual Studio denominado `MenuCommandsPackage`.  
  
2.  En el **información básica de VSPackage** página del asistente, establezca **nombre de la compañía** a `Fabrikam` y **nombre de VSPackage** a `FabrikamMenuCommands`. Elija el botón **Siguiente**.  
  
3.  En la siguiente página, seleccione **comando de menú** y, a continuación, elija **siguiente**.  
  
4.  En la página siguiente, establezca **nombre de comando** a `Fabrikam Command` y **identificador de comando** a `cmdidFabrikamCommand`y, a continuación, elija **siguiente**.  
  
5.  En el **seleccionar opciones de proyecto de prueba** página, desactive las opciones de prueba y, a continuación, elija el **finalizar** botón.  
  
6.  En el proyecto ShellExtensionsVSIX, abra el archivo source.extension.vsixmanifest.  
  
     El **activos** sección debe contener una entrada para el proyecto VSShellStub.AboutBoxPackage.  
  
7.  Elija la **New** botón.  
  
8.  En el **Agregar nuevo activo** ventana, en el **tipo** lista, seleccione **Microsoft.VisualStudio.VsPackage**.  
  
9. En el **origen** lista, asegúrese de que **un proyecto en la solución actual** está seleccionada. En el **proyecto** cuadro de lista, seleccione **MenuCommandsPackage**.  
  
10. Guarde y cierre el archivo.  
  
11. Recompile la solución e iniciar la depuración del shell aislado.  
  
12. En la barra de menús, elija **herramientas** menú y, a continuación, **comando Fabrikam**.  
  
     Debería aparecer un cuadro de mensaje.  
  
13. Detenga la depuración de la aplicación.  
  
## <a name="adding-a-mef-component-part"></a>Agregar un elemento de componente MEF  
 Los pasos siguientes muestran cómo agregar un elemento de componente MEF en la aplicación de shell aislado.  
  
#### <a name="to-add-a-mef-component"></a>Para agregar un componente MEF  
  
1.  En el **Agregar nuevo proyecto** cuadro de diálogo **Visual C#**, **extensibilidad**, utilice el **margen del Editor** plantilla para agregar un proyecto. Denomínelo `ShellEditorMargin`.  
  
2.  En el proyecto ShellExtensionsVSIX, abra el archivo Source.extension.vsixmanifest en la vista Diseño, no en la vista de código.  
  
3.  En el `Asset` sección, elija **agregar contenido**.  
  
4.  En el **Agregar nuevo activo** ventana, en el **tipo** lista, seleccione **Microsoft.VisualStudio.MefComponent**.  
  
5.  En el **origen** lista, asegúrese de que **un proyecto en la solución actual** está seleccionada. En el **proyecto** cuadro de lista, seleccione **ShellEditorMargin**.  
  
6.  Guarde y cierre el archivo.  
  
7.  Recompile la solución e iniciar la depuración del shell aislado.  
  
8.  Abra un archivo de texto.  
  
     Un margen de color verde que contiene las palabras "Hello world!" se debe mostrar en la parte inferior de la ventana de archivo de texto.  
  
9. Detenga la depuración de la aplicación.  
  
## <a name="adding-a-generic-vsix-project"></a>Agregar un proyecto VSIX genérico  
  
#### <a name="to-add-a-generic-vsix-project"></a>Para agregar un proyecto VSIX genérico  
  
1.  En el **Agregar nuevo proyecto** cuadro de diálogo **Visual C#**, **extensibilidad**, utilice el **VSIXProject** plantilla para agregar un proyecto. Denomínelo `EmptyVSIX`.  
  
2.  En el proyecto ShellExtensionsVSIX, abra el archivo Source.extensions.vsixmanifest en la vista Diseño, no en la vista de código.  
  
3.  En el `Assets` sección, elija **New**.  
  
4.  En el **Agregar nuevo activo** ventana, en el **tipo** lista, seleccione el tipo de contenido que desea agregar.  
  
5.  En **origen**, asegúrese de que el **un proyecto de la solución actual** está seleccionada. En el cuadro de lista, seleccione el nombre del proyecto VSIX.  
  
6.  Guarde y cierre el archivo.  
  
7.  Si este proyecto incluye código compilado, debe editar el proyecto para que el ensamblado se incluye en la salida.  
  
    1.  Descargue el proyecto VSIX y abra el archivo de proyecto.  
  
    2.  En la primera `<PropertyGroup>` bloquear, cambie el valor de `<CopyBuildOutputToOutputDirectory>` a `true`.  
  
    3.  Guardar y recargar el proyecto.  
  
8.  Compile y ejecute la solución.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: creación una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

