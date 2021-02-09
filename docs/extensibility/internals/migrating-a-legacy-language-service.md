---
title: Migración de un servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre cómo actualizar un servicio de lenguaje a la versión más reciente de Visual Studio actualizando el proyecto y agregando un archivo source. Extension. vsixmanifest.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a0e20c77a1c8a81a29691079ace1e4751135560
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895692"
---
# <a name="migrating-a-legacy-language-service"></a>Migración de un servicio de lenguaje heredado
Puede migrar un servicio de lenguaje heredado a una versión posterior de Visual Studio actualizando el proyecto y agregando un archivo source. Extension. vsixmanifest al proyecto. El propio servicio de lenguaje seguirá funcionando como antes, ya que el editor de Visual Studio lo adapta.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar un servicio de lenguaje, vea [Editor y extensiones del servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migración de una solución de servicio de lenguaje de Visual Studio 2008 a una versión posterior
 En los pasos siguientes se muestra cómo adaptar un ejemplo de Visual Studio 2008 llamado RegExLanguageService. Puede encontrar este ejemplo en una instalación del SDK de Visual Studio 2008, en la carpeta \VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ de la *ruta de instalación de Visual Studio SDK*.

> [!IMPORTANT]
> Si el servicio de lenguaje no define los colores, debe establecer explícitamente en <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` en el VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Para migrar un servicio de lenguaje de Visual Studio 2008 a una versión posterior

1. Instale las versiones más recientes de Visual Studio y el SDK de Visual Studio. Para obtener más información sobre las formas de instalar el SDK, vea [instalar el SDK de Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).

2. Edite el archivo RegExLangServ. csproj (sin cargarlo en Visual Studio).

     En el `Import` nodo que hace referencia al archivo Microsoft. VsSDK. targets, reemplace el valor por el texto siguiente.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Guarde el archivo y ciérrelo.

4. Abra la solución RegExLangServ. sln.

5. Aparece la ventana de **actualización unidireccional** . Haga clic en **OK**.

6. Actualice las propiedades del proyecto. Para abrir la ventana **propiedades del proyecto** , seleccione el nodo del proyecto en el **Explorador de soluciones**, haga clic con el botón derecho y seleccione **propiedades**.

    - En la pestaña **aplicación** , cambie **plataforma de destino** a **4.6.1**.

    - En la pestaña **depurar** , en el cuadro **programa externo de inicio** , escriba **\<Visual Studio installation path>\Common7\IDE\devenv.exe.**

         En el cuadro argumentos de la **línea de comandos** , escriba/**rootsuffix exp**.

7. Actualice las referencias siguientes:

    - Quite la referencia a Microsoft.VisualStudio.Shell.9.0.dll y, a continuación, agregue referencias a Microsoft.VisualStudio.Shell.14.0.dll y Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Quite la referencia a Microsoft.VisualStudio.Package.LanguageService.9.0.dll y, a continuación, agregue una referencia a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Agregue una referencia a Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Abra el archivo VsPkg.cs y cambie el valor del `DefaultRegistryRoot` atributo a

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. El ejemplo original no registra su servicio de lenguaje, por lo que debe agregar el atributo siguiente a VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Debe agregar un archivo source. Extension. vsixmanifest.

    - Copie este archivo desde una extensión existente al directorio del proyecto. (Una forma de obtener este archivo es crear un proyecto VSIX (en **archivo**, haga clic en **nuevo** y, a continuación, haga clic en **proyecto**. En Visual Basic o C#, haga clic en **extensibilidad** y, a continuación, seleccione **Proyecto VSIX**).

    - Agregue el archivo al proyecto.

    - En las **propiedades** del archivo, establezca **acción de compilación** en **ninguno**.

    - Abra el archivo con el **Editor de manifiestos de VSIX**.

    - Cambie los campos siguientes:

    - **ID.**: RegExLangServ

    - **Nombre del producto**: RegExLangServ

    - **Descripción**: un servicio de lenguaje de expresiones regulares.

    - En **activos**, haga clic en **nuevo**, seleccione el **tipo** en **Microsoft. VisualStudio. VsPackage**, establezca el **origen** en **un proyecto en la solución actual** y, a continuación, establezca el **proyecto** en **RegExLangServ**.

    - Guarde y cierre el archivo.

11. Compile la solución. Los archivos compilados se implementan en **%userprofile%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ \\**.

12. Inicie la depuración. Se abre una segunda instancia de Visual Studio.

## <a name="see-also"></a>Vea también
- [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)
