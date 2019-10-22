---
title: Migrar un servicio de lenguaje heredado | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6c5d665367f2d5af9e2dd6d2a7d664e50f4830
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434375"
---
# <a name="migrating-a-legacy-language-service"></a>Migración de un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Puede migrar un servicio de lenguaje heredado a una versión posterior de Visual Studio mediante la actualización del proyecto y agregar un archivo source.extension.vsixmanifest al proyecto. El propio servicio de lenguaje continuarán funcionando como antes, porque adapta el editor de Visual Studio.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrar una solución de servicio de lenguaje de Visual Studio 2008 a una versión posterior  
 Los pasos siguientes muestran cómo adaptar un ejemplo de Visual Studio 2008 denominado RegExLanguageService. Puede encontrar en este ejemplo en una instalación de SDK de Visual Studio 2008, el *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ carpeta.  
  
> [!IMPORTANT]
> Si el servicio de lenguaje no define los colores, debe establecer explícitamente <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> a `true` en el VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Para migrar un servicio de lenguaje de Visual Studio 2008 a una versión posterior  
  
1. Instale las versiones más recientes de Visual Studio y Visual Studio SDK. Para obtener más información sobre cómo instalar el SDK, consulte [instalar el SDK de Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2. Editar el archivo RegExLangServ.csproj (sin carga en Visual Studio.  
  
     En el `Import` nodo al que hace referencia al archivo Microsoft.VsSDK.targets, reemplace el valor con el siguiente texto.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3. Guarde el archivo y, a continuación, ciérrelo.  
  
4. Abra la solución RegExLangServ.sln.  
  
5. El **actualización unidireccional** aparecerá la ventana. Haga clic en **Aceptar**.  
  
6. Actualizar las propiedades del proyecto. Abra el **las propiedades del proyecto** ventana seleccionando el nodo del proyecto en el **el Explorador de soluciones**, hacer clic y seleccione **propiedades**.  
  
    - En el **aplicación** , modifique **.NET framework de destino** a **4.6.1**.  
  
    - En el **depurar** ficha la **iniciar programa externo** , escriba  **\<ruta de instalación de Visual Studio > \Common7\IDE\devenv.exe.** .  
  
         En el **argumentos de línea de comandos** , escriba /**rootsuffix Exp**.  
  
7. Actualizar las referencias siguientes:  
  
    - Quite la referencia a Microsoft.VisualStudio.Shell.9.0.dll, a continuación, agregue referencias a Microsoft.VisualStudio.Shell.14.0.dll y Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    - Quite la referencia a Microsoft.VisualStudio.Package.LanguageService.9.0.dll, a continuación, agregue una referencia a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    - Agregue una referencia a Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8. Abra el archivo VsPkg.cs y cambie el valor de la `DefaultRegistryRoot` atributo  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. El ejemplo original no registrar su servicio de lenguaje, por lo que debe agregar el atributo siguiente a VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Debe agregar un archivo source.extension.vsixmanifest.  
  
    - Copie este archivo una extensión existente al directorio del proyecto. (Una forma de obtener este archivo consiste en crear un proyecto de VSIX (bajo **archivo**, haga clic en **New**, a continuación, haga clic en **proyecto**. Haga clic en Visual Basic o C# **extensibilidad**, a continuación, seleccione **proyecto VSIX**.)  
  
    - Agregue el archivo al proyecto.  
  
    - En el archivo **propiedades**, establezca **acción de compilación** a **ninguno**.  
  
    - Abra el archivo con el **Editor de manifiestos VSIX**.  
  
    - Cambiar los campos siguientes:  
  
    - **ID**: RegExLangServ  
  
    - **Nombre de producto**: RegExLangServ  
  
    - **Descripción**: Un servicio de lenguaje de expresión regular.  
  
    - En **activos**, haga clic en **New**, seleccione el **tipo** a **Microsoft.VisualStudio.VsPackage**, establezca el **origen** a **un proyecto de la solución actual**y, a continuación, establezca el **proyecto** a **RegExLangServ**.  
  
    - Guarde y cierre el archivo.  
  
11. Compile la solución. Se implementan los archivos compilados en **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\** .  
  
12. Inicie la depuración. Puede abrir una segunda instancia de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)
