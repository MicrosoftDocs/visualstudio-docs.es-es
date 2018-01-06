---
title: Migrar un servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f5f7cff29dd368acbbc3f599ec0cf623343031f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-a-legacy-language-service"></a>Migrar un servicio de lenguaje heredado
Puede migrar un servicio de lenguaje heredado a una versión posterior de Visual Studio mediante la actualización del proyecto y agregar un archivo source.extension.vsixmanifest al proyecto. El propio servicio de lenguaje continuarán funcionando como antes, porque el editor de Visual Studio adapta a él.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrar una solución de servicio de lenguaje de Visual Studio 2008 a una versión posterior  
 Los pasos siguientes muestran cómo adaptar un ejemplo de Visual Studio 2008 denominado RegExLanguageService. Puede encontrar este ejemplo en una instalación de SDK de Visual Studio 2008, en la *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ carpeta.  
  
> [!IMPORTANT]
>  Si el servicio de lenguaje no define los colores, debe establecer explícitamente <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> a `true` en el VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Para migrar un servicio de lenguaje de Visual Studio 2008 a una versión posterior  
  
1.  Instale las versiones más recientes de Visual Studio y el SDK de Visual Studio. Para obtener más información acerca de formas de instalar el SDK, consulte [instalar el SDK de Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Edite el archivo RegExLangServ.csproj (sin cargarlos en Visual Studio.  
  
     En el `Import` nodo que hace referencia al archivo Microsoft.VsSDK.targets, reemplace el valor con el siguiente texto.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Guarde el archivo y, a continuación, ciérrelo.  
  
4.  Abra la solución RegExLangServ.sln.  
  
5.  El **actualización unidireccional** aparecerá la ventana. Haga clic en **Aceptar**.  
  
6.  Actualizar las propiedades del proyecto. Abra la **propiedades del proyecto** ventana, seleccione el nodo de proyecto en el **el Explorador de soluciones**, clic y seleccione **propiedades**.  
  
    -   En el **aplicación** , modifique **.NET framework de destino** a **4.6.1**.  
  
    -   En el **depurar** ficha la **iniciar programa externo** , escriba  **\<ruta de instalación de Visual Studio > \Common7\IDE\devenv.exe.**.  
  
         En el **argumentos de línea de comandos** , escriba /**/rootsuffix Exp**.  
  
7.  Actualizar las referencias siguientes:  
  
    -   Quite la referencia a Microsoft.VisualStudio.Shell.9.0.dll, a continuación, agregue referencias a Microsoft.VisualStudio.Shell.14.0.dll y Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Quite la referencia a Microsoft.VisualStudio.Package.LanguageService.9.0.dll, a continuación, agregue una referencia a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Agregue una referencia a Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Abra el archivo VsPkg.cs y cambie el valor de la `DefaultRegistryRoot` atribuir a  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. El ejemplo original no registra su servicio de lenguaje, por lo que debe agregar el atributo siguiente a VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Debe agregar un archivo source.extension.vsixmanifest.  
  
    -   Copie este archivo desde una extensión existente en el directorio del proyecto. (Es una manera de obtener este archivo crear un proyecto VSIX (bajo **archivo**, haga clic en **New**, a continuación, haga clic en **proyecto**. Haga clic en Visual Basic o C# **extensibilidad**, a continuación, seleccione **proyecto VSIX**.)  
  
    -   Agregue el archivo al proyecto.  
  
    -   En el archivo **propiedades**, establezca **acción de compilación** a **ninguno**.  
  
    -   Abra el archivo con el **Editor de manifiestos VSIX**.  
  
    -   Cambiar los campos siguientes:  
  
    -   **Id. de**: RegExLangServ  
  
    -   **Nombre de producto**: RegExLangServ  
  
    -   **Descripción**: un servicio de lenguaje de expresión regular.  
  
    -   En **activos**, haga clic en **New**, seleccione la **tipo** a **Microsoft.VisualStudio.VsPackage**, establezca el **origen** a **un proyecto de la solución actual**y, a continuación, establezca el **proyecto** a **RegExLangServ**.  
  
    -   Guarde y cierre el archivo.  
  
11. Compile la solución. Los archivos generados se implementan en **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Inicie la depuración. Abre una segunda instancia de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)