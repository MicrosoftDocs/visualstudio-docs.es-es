---
title: Acceso al objeto DTE desde una extensión del editor
description: Obtenga información sobre cómo acceder al objeto DTE desde una extensión del editor mediante el ejemplo de código de este tutorial.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 094a37960fa5b32d018eebe3becee4fde43cc392
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905129"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Tutorial: Acceso al objeto DTE desde una extensión del editor

En VSPackages, puede obtener el objeto DTE llamando al método <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> con el tipo del objeto DTE. En Managed Extensibility Framework (MEF), puede importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> y después llamar al método <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> con un tipo de <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Requisitos previos

Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtiene el objeto DTE.

1. Cree un proyecto VSIX de C# y asígnele el nombre **DTETest**. Agregue una plantilla de elemento **Clasificador de editor** y asígnele el nombre **DTETest**.

   Para obtener más información, vea [Creación de una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Agregue las referencias de ensamblado siguientes al proyecto:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. En el archivo *DTETestProvider.cs*, agregue las directivas `using` siguientes:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En la clase `DTETestProvider`, importe un objeto <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. En el método `GetClassifier()`, agregue el código siguiente antes de la instrucción `return`:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Agregue las referencias de ensamblado siguientes al proyecto:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. En el archivo *DTETestProvider.cs*, agregue las directivas `using` siguientes:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En la clase `DTETestProvider`, importe un objeto <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. En el método `GetClassifier()`, agregue el código siguiente antes de la instrucción `return`:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Consulta también

- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
- [Inicio de Visual Studio con DTE](launch-visual-studio-dte.md)
