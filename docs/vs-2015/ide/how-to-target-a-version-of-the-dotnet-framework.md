---
title: Procedimiento Una versión de .NET Framework de destino | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ee322255cbb737aa4503517c599c62c9151937ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782312"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Cómo: Usar como destino una versión de .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se describe cómo se crea un proyecto que tiene como destino una versión de .NET Framework y cómo se modifica la versión de destino en un proyecto de Visual Basic, Visual C# o Visual F# existente.  
  
> [!IMPORTANT]
>  Para obtener información sobre cómo cambiar la versión de destino para los proyectos de C++, consulte [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
 **En este tema**  
  
-   [Especificar una versión de destino al crear un proyecto](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Cambiar la versión de destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Especificar una versión de destino al crear un proyecto  
 Cuando crea un proyecto, la versión destino de .NET Framework las plantillas que se pueden utilizar.  
  
> [!NOTE]
>  En las ediciones Express de Visual Studio, debe crear primero el proyecto y después cambiar el destino, como se describe más adelante en [Cambiar la versión de destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) en este tema.  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>Para especificar una versión de destino al crear un proyecto  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En la lista situada en la parte superior del cuadro de diálogo **Nuevo proyecto**, elija la versión de .NET Framework de destino que quiera especificar para el proyecto.  
  
    > [!NOTE]
    >  Normalmente, solo se instala una versión de .NET Framework junto con Visual Studio. Si desea establecer como destino otra versión, primero debe asegurarse de que está instalada. Consulte [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  En la lista de plantillas instaladas, elija el tipo de proyecto que quiere crear, asigne un nombre al proyecto y después elija el botón **Aceptar**.  
  
     La lista de plantillas muestra únicamente los proyectos que son compatibles con la versión de .NET Framework que ha elegido.  
  
##  <a name="bkmk_existing"></a> Cambiar la versión de destino  
 Puede cambiar la versión de .NET Framework de destino en un proyecto de Visual Basic, Visual C# o Visual F# si sigue este procedimiento.  
  
#### <a name="to-change-the-targeted-version"></a>Para cambiar la versión de destino  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto que quiere cambiar y después elija **Propiedades**.  
  
     ![Propiedades del Explorador de soluciones de Visual Studio](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Para obtener información sobre cómo cambiar la versión de destino para los proyectos de C++, consulte [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
2.  En la columna izquierda de la ventana Propiedades, elija la pestaña **Aplicación**.  
  
     ![Propiedades de aplicación de Visual Studio, pestaña Aplicación](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Después de crear una aplicación de la Tienda Windows, no puede cambiar la versión de destino de Windows ni de .NET Framework.  
  
3.  En la lista **Plataforma de destino**, elija la versión que quiera.  
  
4.  En el cuadro de diálogo de comprobación que aparece, elija el botón **Sí**.  
  
     Se descarga el proyecto. Cuando se vuelva a cargar, la versión de .NET Framework de destino será la que acaba de elegir.  
  
    > [!NOTE]
    >  Si el código contiene referencias a una versión de .NET Framework distinta de la que indicó, pueden aparecer mensajes de error al compilar o ejecutar el código. Para resolver estos errores, deberá modificar las referencias. Consulte [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../ide/visual-studio-multi-targeting-overview.md)   
 [Especificar una versión de .NET Framework para sitios web](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Configurar proyectos](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)
