---
title: Tener acceso al objeto DTE desde una extensión del editor
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3e21ea3d05350a59d62fc9da9e0387f072ec16
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878200"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Tutorial: Tener acceso al objeto DTE desde una extensión del editor

En los paquetes VSPackage, puede obtener el objeto DTE mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método con el tipo del objeto DTE. En las extensiones de Managed Extensibility Framework (MEF), puede importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> y, a continuación, llame a la <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método con un tipo de <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Requisitos previos

Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtener el objeto DTE

1. Crear un C# VSIX de proyecto y asígnele el nombre **DTETest**. Agregar un **clasificador de Editor** plantilla de elemento y asígnele el nombre **DTETest**.

   Para obtener más información, consulte [crear una extensión con una plantilla de elementos de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Agregue la siguiente referencia de ensamblado al proyecto:

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. En el *DTETestProvider.cs* , agregue la siguiente `using` directivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En el `DTETestProvider` class, importar un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. En el `GetClassifier()` método, agregue el código siguiente antes de la `return` instrucción:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Agregue las siguientes referencias de ensamblado al proyecto:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. En el *DTETestProvider.cs* , agregue la siguiente `using` directivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En el `DTETestProvider` class, importar un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. En el `GetClassifier()` método, agregue el código siguiente antes de la `return` instrucción:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Vea también

- [Puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
- [Inicie Visual Studio con el DTE](launch-visual-studio-dte.md)