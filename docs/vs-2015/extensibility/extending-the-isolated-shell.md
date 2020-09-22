---
title: Extender el shell aislado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842650"
---
# <a name="extending-the-isolated-shell"></a>Ampliación de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender el shell aislado de Visual Studio agregando un VSPackage, una parte del componente Managed Extensibility Framework (MEF) o un proyecto VSIX genérico a la aplicación de Shell aislado.  
  
> [!NOTE]
> En los pasos siguientes se presupone que ha creado una aplicación básica de Shell aislado mediante la plantilla de proyecto aislado de Visual Studio Shell. Para obtener más información sobre esta plantilla de proyecto, vea [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Ubicaciones de la plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto del paquete de Visual Studio puede encontrarse en tres ubicaciones diferentes en el cuadro de diálogo **Nuevo proyecto** :  
  
1. En **Visual Basic**, **extensibilidad**. El lenguaje predeterminado del proyecto es Visual Basic.  
  
2. En **Visual C#**, **extensibilidad**. El lenguaje predeterminado del proyecto es C#.  
  
3. En **otros tipos de proyectos**, **extensibilidad**. El lenguaje predeterminado del proyecto es C++.  
  
## <a name="adding-a-vspackage"></a>Agregar un VSPackage  
 Puede Agregar un VSPackage a la aplicación de Shell aislado. En los pasos siguientes se muestra cómo crear uno que agrega comandos de menú.  
  
#### <a name="to-add-a-new-vspackage"></a>Para agregar un VSPackage nuevo  
  
1. Agregue un proyecto de paquete de Visual Studio denominado `MenuCommandsPackage` .  
  
2. En la página **información básica de VSPackage** del asistente, establezca el nombre de la **compañía** en `Fabrikam` y **el nombre del VSPackage** en `FabrikamMenuCommands` . Elija el botón **Siguiente**.  
  
3. En la página siguiente, seleccione **comando de menú** y, a continuación, elija **siguiente**.  
  
4. En la página siguiente, establezca **nombre de comando** en `Fabrikam Command` y ID. de **comando** en y, `cmdidFabrikamCommand` a continuación, elija **siguiente**.  
  
5. En la página **seleccionar opciones del proyecto de prueba** , desactive las opciones de prueba y, a continuación, elija el botón **Finalizar** .  
  
6. En el proyecto ShellExtensionsVSIX, abra el archivo source. Extension. vsixmanifest.  
  
     La sección **assets** debe contener una entrada para el proyecto VSShellStub. AboutBoxPackage.  
  
7. Elija el botón **nuevo** .  
  
8. En la ventana **Agregar nuevo recurso** , en la lista **tipo** , seleccione **Microsoft. VisualStudio. VsPackage**.  
  
9. En la lista **origen** , asegúrese de que se ha seleccionado **un proyecto en la solución actual** . En el cuadro de lista **proyecto** , seleccione **MenuCommandsPackage**.  
  
10. Guarde y cierre el archivo.  
  
11. Recompile la solución e inicie la depuración del shell aislado.  
  
12. En la barra de menús, elija Menú **herramientas** y, a continuación, **comando de Fabrikam**.  
  
     Debería aparecer un cuadro de mensaje.  
  
13. Detenga la depuración de la aplicación.  
  
## <a name="adding-a-mef-component-part"></a>Agregar una parte del componente MEF  
 En los pasos siguientes se muestra cómo agregar una parte del componente MEF a la aplicación de Shell aislado.  
  
#### <a name="to-add-a-mef-component"></a>Para agregar un componente MEF  
  
1. En el cuadro de diálogo **Agregar nuevo proyecto** , en **Visual C#**, **extensibilidad**, use la plantilla de **margen del editor** para agregar un proyecto. Asígnele el nombre `ShellEditorMargin`.  
  
2. En el proyecto ShellExtensionsVSIX, abra el archivo source. Extension. vsixmanifest en el Vista de diseño, no en la vista de código.  
  
3. En la `Asset` sección, elija **agregar contenido**.  
  
4. En la ventana **Agregar nuevo recurso** , en la lista **tipo** , seleccione **Microsoft. VisualStudio. MefComponent**.  
  
5. En la lista **origen** , asegúrese de que se ha seleccionado **un proyecto en la solución actual** . En el cuadro de lista **proyecto** , seleccione **ShellEditorMargin**.  
  
6. Guarde y cierre el archivo.  
  
7. Recompile la solución e inicie la depuración del shell aislado.  
  
8. Abra un archivo de texto.  
  
     Un margen verde que contiene las palabras "Hello World!" se debe mostrar en la parte inferior de la ventana del archivo de texto.  
  
9. Detenga la depuración de la aplicación.  
  
## <a name="adding-a-generic-vsix-project"></a>Agregar un proyecto de VSIX genérico  
  
#### <a name="to-add-a-generic-vsix-project"></a>Para agregar un proyecto VSIX genérico  
  
1. En el cuadro de diálogo **Agregar nuevo proyecto** , en **Visual C#**, **extensibilidad**, use la plantilla **VSIXProject** para agregar un proyecto. Asígnele el nombre `EmptyVSIX`.  
  
2. En el proyecto ShellExtensionsVSIX, abra el archivo source. Extensions. vsixmanifest en el Vista de diseño, no en la vista de código.  
  
3. En la `Assets` sección, elija **nuevo**.  
  
4. En la ventana **Agregar nuevo recurso** , en la lista **tipo** , seleccione el tipo de contenido que desea agregar.  
  
5. En **origen**, asegúrese de que esté seleccionada la opción **un proyecto en la solución actual** . En el cuadro de lista, seleccione el nombre del Proyecto VSIX.  
  
6. Guarde y cierre el archivo.  
  
7. Si este proyecto incluye código compilado, debe modificar el proyecto para que el ensamblado se incluya en la salida.  
  
    1. Descargue el Proyecto VSIX y abra el archivo de proyecto.  
  
    2. En el primer `<PropertyGroup>` bloque, cambie el valor de `<CopyBuildOutputToOutputDirectory>` a `true` .  
  
    3. Guarde y vuelva a cargar el proyecto.  
  
8. Compile y ejecute la solución.  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial: creación una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
