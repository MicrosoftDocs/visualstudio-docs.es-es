---
title: Acceso al objeto DTE desde una extensión de editor
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269085"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Tutorial: acceso al objeto DTE desde una extensión de editor

En VSPackages, puede obtener el objeto DTE llamando al método <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> con el tipo del objeto DTE. En las extensiones de Managed Extensibility Framework (MEF), puede importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> y, a continuación, llamar al método <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> con un tipo de <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Requisitos previos

Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtiene el objeto DTE.

1. Cree un C# Proyecto VSIX y asígnele el nombre **DTETest**. Agregue una plantilla de elemento **clasificador de editor** y asígnele el nombre **DTETest**.

   Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Agregue las siguientes referencias de ensamblado al proyecto:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. En el archivo *DTETestProvider.CS* , agregue las siguientes directivas de `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En la clase `DTETestProvider`, importe un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

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

2. Agregue las siguientes referencias de ensamblado al proyecto:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. En el archivo *DTETestProvider.CS* , agregue las siguientes directivas de `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En la clase `DTETestProvider`, importe un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. En el método `GetClassifier()`, agregue el código siguiente antes de la instrucción `return`:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Vea también

- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
- [Iniciar Visual Studio mediante DTE](launch-visual-studio-dte.md)
