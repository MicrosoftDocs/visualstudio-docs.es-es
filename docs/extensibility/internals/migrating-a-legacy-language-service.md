---
title: Migración de un servicio de lenguaje heredado (Legacy Language Service) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707107"
---
# <a name="migrating-a-legacy-language-service"></a>Migración de un servicio de lenguaje heredado
Puede migrar un servicio de lenguaje heredado a una versión posterior de Visual Studio actualizando el proyecto y agregando un archivo source.extension.vsixmanifest al proyecto. El propio servicio de lenguaje seguirá funcionando como antes, porque el editor de Visual Studio lo adapta.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva forma de implementar un servicio de lenguaje, vea [Extensiones](../../extensibility/editor-and-language-service-extensions.md)de servicio de editor y lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migración de una solución de servicio de lenguaje de Visual Studio 2008 a una versión posterior
 En los pasos siguientes se muestra cómo adaptar un ejemplo de Visual Studio 2008 denominado RegExLanguageService. Puede encontrar este ejemplo en una instalación del SDK de Visual Studio 2008, en la ruta de instalación del SDK de *Visual Studio.*

> [!IMPORTANT]
> Si el servicio de lenguaje no define <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> colores, debe establecer explícitamente `true` en el VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Para migrar un servicio de lenguaje de Visual Studio 2008 a una versión posterior

1. Instale las versiones más recientes de Visual Studio y el SDK de Visual Studio. Para obtener más información acerca de las formas de instalar el SDK, vea [Instalar el SDK](../../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

2. Edite el archivo RegExLangServ.csproj (sin cargarlo en Visual Studio.

     En `Import` el nodo que hace referencia al archivo Microsoft.VsSDK.targets, reemplace el valor por el texto siguiente.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Guarde el archivo y, a continuación, ciérrelo.

4. Abra la solución RegExLangServ.sln.

5. Aparece la ventana **Actualización unidireccional.** Haga clic en **OK**.

6. Actualice las propiedades del proyecto. Abra la ventana Propiedades del **proyecto** seleccionando el nodo del proyecto en el **Explorador**de soluciones , haciendo clic con el botón derecho y seleccionando **Propiedades**.

    - En la pestaña **Aplicación,** cambie Marco de **destino** a **4.6.1**.

    - En la pestaña **Depurar,** en el cuadro **Iniciar programa externo** , escriba ** \<Ruta**de instalación de Visual Studio>.

         En el cuadro **Argumentos** de línea de comandos , escriba /**rootsuffix Exp**.

7. Actualice las siguientes referencias:

    - Quite la referencia a Microsoft.VisualStudio.Shell.9.0.dll y, a continuación, agregue referencias a Microsoft.VisualStudio.Shell.14.0.dll y Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Quite la referencia a Microsoft.VisualStudio.Package.LanguageService.9.0.dll y, a continuación, agregue una referencia a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Agregue una referencia a Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Abra el archivo VsPkg.cs y `DefaultRegistryRoot` cambie el valor del atributo a

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. El ejemplo original no registra su servicio de lenguaje, por lo que debe agregar el siguiente atributo a VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Debe agregar un archivo source.extension.vsixmanifest.

    - Copie este archivo de una extensión existente en el directorio del proyecto. (Una forma de obtener este archivo es crear un proyecto VSIX (en **Archivo**, haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**. En Visual Basic o en C, haga clic en **Extensibilidad**y, a continuación, seleccione **Proyecto VSIX**.)

    - Agregue el archivo al proyecto.

    - En Propiedades **del**archivo , establezca Acción de **compilación** en **Ninguno**.

    - Abra el archivo con el Editor de **manifiestos VSIX**.

    - Cambie los siguientes campos:

    - **ID**: RegExLangServ

    - **Nombre del producto**: RegExLangServ

    - **Descripción**: Un servicio de lenguaje de expresiones regulares.

    - En **Assets**, haga clic en **New**, seleccione **Type** to **Microsoft.VisualStudio.VsPackage**, establezca **Source** en A project en **la solución actual**y, a continuación, establezca **Project** en **RegExLangServ**.

    - Guarde y cierre el archivo.

11. Compile la solución. Los archivos compilados se implementan en **%USERPROFILE%-AppData-Local-Microsoft-VisualStudio-14.0Exp-Extensions-MSIT-RegExLangServ\\**.

12. Inicie la depuración. Se ha abierto una segunda instancia de Visual Studio.

## <a name="see-also"></a>Vea también
- [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)
