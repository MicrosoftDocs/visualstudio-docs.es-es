---
title: Acceda al objeto DTE desde una extensión de editor
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697657"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Tutorial: Acceda al objeto DTE desde una extensión de editor

En VSPackages, puede obtener el objeto <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE llamando al método con el tipo de la DTE objeto. En extensiones de Managed Extensibility Framework <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (MEF), <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> puede importar <xref:EnvDTE.DTE>y, a continuación, llamar al método con un tipo de .

## <a name="prerequisites"></a>Prerrequisitos

Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtiene el objeto DTE.

1. Cree un proyecto vSIX de C- y asíse **DTETest**. Agregue una plantilla de elemento **Clasificador** de editor y **asísaber, asísaber, DTETest**.

   Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

::: moniker range=">=vs-2019"

2. Agregue las siguientes referencias de ensamblado al proyecto:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. En el archivo *DTETestProvider.cs,* agregue las siguientes `using` directivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En `DTETestProvider` la clase, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>importe un archivo .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. En `GetClassifier()` el método, agregue el `return` código siguiente antes de la instrucción:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Agregue las siguientes referencias de ensamblado al proyecto:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. En el archivo *DTETestProvider.cs,* agregue las siguientes `using` directivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En `DTETestProvider` la clase, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>importe un archivo .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. En `GetClassifier()` el método, agregue el `return` código siguiente antes de la instrucción:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Vea también

- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
- [Inicio de Visual Studio con DTE](launch-visual-studio-dte.md)
