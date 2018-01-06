---
title: "Tutorial: Obtener acceso a los del objeto DTE desde una extensión del Editor | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af14fa5f9a76e08a1fba3355e9391ce8229bd652
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Tutorial: Obtener acceso a los del objeto DTE desde una extensión del Editor
En los paquetes VSPackage, puede obtener el objeto DTE mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método con el tipo del objeto DTE. En las extensiones de Managed Extensibility Framework (MEF), puede importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> y, a continuación, llame a la <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método con un tipo de <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Obteniendo el objeto DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Para obtener el objeto DTE de ServiceProvider  
  
1.  Cree un proyecto de C# VSIX denominado `DTETest`. Agregar una plantilla de elementos de clasificador de Editor y asígnele el nombre `DTETest`. Para obtener más información, consulte [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Agregue las siguientes referencias de ensamblado al proyecto:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Vaya al archivo DTETest.cs y agregue el siguiente `using` directivas:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  En el `GetDTEProvider` de clases, importar un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
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