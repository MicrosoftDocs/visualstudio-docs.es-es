---
title: 'Tutorial: Acceso al objeto DTE desde una extensión del Editor | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2669571fee0ea9f43c06ba9ec7526d0716931fe0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239933"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Tutorial: Acceso al objeto DTE desde una extensión del editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En los paquetes VSPackage, puede obtener el objeto DTE mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método con el tipo del objeto DTE. En las extensiones de Managed Extensibility Framework (MEF), puede importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> y, a continuación, llame a la <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método con un tipo de <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Obteniendo el objeto DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Para obtener el objeto DTE de ServiceProvider  
  
1.  Cree un proyecto de VSIX de C# denominado `DTETest`. Agregar una plantilla de elemento de clasificador de Editor y asígnele el nombre `DTETest`. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Agregue las siguientes referencias de ensamblado al proyecto:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Vaya al archivo DTETest.cs y agregue la siguiente `using` directivas:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  En el `GetDTEProvider` class, importar un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  En el método `GetClassifier()`, agregue el siguiente código.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Si tiene que usar el <xref:EnvDTE80.DTE2> interfaz, puede convertir el objeto DTE.  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)

