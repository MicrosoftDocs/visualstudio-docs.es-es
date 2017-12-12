---
title: "Cómo: Usar como destino una versión de .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67145a9aaaf4c01b02bc1cc6db89e375639b4fcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Cómo: Usar como destino una versión de .NET Framework
En este documento se describe cómo se crea un proyecto que tiene como destino una versión de .NET Framework y cómo se modifica la versión de destino en un proyecto de Visual Basic, Visual C# o Visual F# existente.  
  
> [!IMPORTANT]
>  Para obtener información sobre cómo cambiar la versión de destino para los proyectos de C++, consulte [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
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
  
     ![Propiedades del Explorador de soluciones de Visual Studio](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Para obtener información sobre cómo cambiar la versión de destino para los proyectos de C++, consulte [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
2.  En la columna izquierda de la ventana Propiedades, elija la pestaña **Aplicación**.  
  
     ![Propiedades de aplicación de Visual Studio, pestaña Aplicación](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Después de crear una aplicación para UWP, no puede cambiar la versión de destino de Windows ni de .NET Framework.  
  
3.  En la lista **Plataforma de destino**, elija la versión que quiera.  
  
4.  En el cuadro de diálogo de comprobación que aparece, elija el botón **Sí**.  
  
     Se descarga el proyecto. Cuando se vuelva a cargar, la versión de .NET Framework de destino será la que acaba de elegir.  
  
    > [!NOTE]
    >  Si el código contiene referencias a una versión de .NET Framework distinta de la que indicó, pueden aparecer mensajes de error al compilar o ejecutar el código. Para resolver estos errores, deberá modificar las referencias. Consulte [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio](../ide/visual-studio-multi-targeting-overview.md)   
 [Especificar una versión de .NET Framework para sitios web](http://msdn.microsoft.com/Library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Configurar proyectos](http://msdn.microsoft.com/Library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)