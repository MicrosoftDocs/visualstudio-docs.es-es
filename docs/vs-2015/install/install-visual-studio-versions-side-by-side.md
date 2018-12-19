---
title: Instalación de distintas versiones de Visual Studio en paralelo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: be7559fb9bc6a2e028638ae18209a91cde955e7f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056644"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalación de distintas versiones de Visual Studio en paralelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede instalar esta versión de Visual Studio en un equipo que ya tiene una versión anterior instalada. Si se produce un error de instalación, puede usar la [herramienta de recopilación de registros](http://go.microsoft.com/fwlink/?LinkId=262077) para recopilar información sobre los errores de forma que pueda depurar los problemas usted mismo.

> [!NOTE]
> Se recomienda instalar las versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en el orden en que se publicaron. Por ejemplo, instale Visual Studio 2013 antes de instalar Visual Studio 2015.

 Antes de instalar versiones en paralelo, debe tener en cuenta los siguientes puntos:

-   Si usa Visual Studio 2015 para abrir una solución creada en [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], puede volver a abrir y modificar después la solución en la versión anterior siempre y cuando no haya implementado ninguna de las características que son específicas de Visual Studio 2015.

-   Si intenta usar Visual Studio 2015 para abrir una solución creada en [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] o en una versión anterior, es posible que necesite modificar los proyectos y los archivos para que sean compatibles con Visual Studio 2015. Para obtener más información, consulte el [portar, migrar y actualizar proyectos de Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) página.

-   Si se desinstala una versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en un equipo que tiene más de una versión instalada, se quitan las asociaciones de archivo de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para todas las versiones. Estas asociaciones de archivo se pueden volver a asignar mediante el botón **Restaurar asociaciones de archivo** que está disponible en la página **Entorno**, **General** del cuadro de diálogo [Opciones](../ide/reference/general-environment-options-dialog-box.md) .

-   Visual Studio no actualiza automáticamente las extensiones porque no todas las extensiones son compatibles. Debe reinstalar las extensiones desde la [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkId=178891) o el Editor de software.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versiones de .NET Framework e instalaciones en paralelo

-   Los proyectos de Visual Basic, Visual C# y Visual F# utilizan la opción **Versión de .NET Framework de destino** del **Diseñador de proyectos** para especificar la versión de .NET Framework que utiliza un proyecto. En un proyecto de C++, se puede cambiar manualmente la versión de .NET Framework de destino si se modifica el archivo .vcxproj. Para obtener más información, consulte [compatibilidad de versiones](http://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).

     Cuando se crea un proyecto, se puede especificar la versión de .NET Framework a la que se dirige el proyecto en la lista **.NET Framework** del cuadro de diálogo **Nuevo proyecto** .

     Para obtener información específica del lenguaje, vea el tema correspondiente en la tabla siguiente.

    |Lenguaje|Tema|
    |--------------|-----------|
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Página de aplicación, Diseñador de proyectos (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|
    |Visual C#|[Página de aplicación, Diseñador de proyectos (C#)](../ide/reference/application-page-project-designer-csharp.md)|
    |Visual F#|[Configurar proyectos](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|
    |C++|[Cómo: Modificar la plataforma de destino y el conjunto de herramientas de plataforma](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Ejecutar una aplicación de JScript en una versión anterior de Common Language Runtime](http://msdn.microsoft.com/en-us/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>Vea también

- [Instalar Visual Studio](../install/install-visual-studio-2015.md)
- [Portar, migrar y actualizar proyectos de Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](http://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)