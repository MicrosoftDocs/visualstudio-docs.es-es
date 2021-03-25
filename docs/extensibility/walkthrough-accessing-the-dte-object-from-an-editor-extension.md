---
title: Acceso al objeto DTE desde una extensión de editor
description: Obtenga información sobre cómo tener acceso al objeto DTE desde una extensión de editor mediante el ejemplo de código de este tutorial.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7035842f608428f149dd2c0965b4792afa25db67
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062075"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Tutorial: acceso al objeto DTE desde una extensión de editor

En VSPackages, puede obtener el objeto DTE llamando al <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método con el tipo del objeto DTE. En las extensiones de Managed Extensibility Framework (MEF), puede importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> y, a continuación, llamar al <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método con un tipo de <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Requisitos previos

Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtiene el objeto DTE.

1. Cree un proyecto VSIX de C# y asígnele el nombre **DTETest**. Agregue una plantilla de elemento **clasificador de editor** y asígnele el nombre **DTETest**.

   Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Agregue las siguientes referencias de ensamblado al proyecto:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. immutable. 10.0

3. En el archivo *DTETestProvider. CS* , agregue las siguientes `using` directivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En la `DTETestProvider` clase, importe un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

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
   - Microsoft. VisualStudio. Shell. Framework

3. En el archivo *DTETestProvider. CS* , agregue las siguientes `using` directivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. En la `DTETestProvider` clase, importe un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. En el `GetClassifier()` método, agregue el código siguiente antes de la `return` instrucción:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Consulte también

- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
- [Inicio de Visual Studio con DTE](launch-visual-studio-dte.md)
