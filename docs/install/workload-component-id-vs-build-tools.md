---
title: Identificadores de componente y carga de trabajo de Visual Studio Build Tools 2017 | Microsoft Docs
description: "Uso de identificadores de componente y carga de trabajo de Visual Studio para crear aplicaciones clásicas basadas en Windows"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 08/30/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 96018963278cd1d53b226473baade41da1e98111
ms.openlocfilehash: 86ac70e66b581a2e70dc8efa185b1e61d7d0204c
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Directorio de componentes de Visual Studio Build Tools 2017

Las tablas de esta página presentan los identificadores que puede usar para instalar Visual Studio mediante la línea de comandos. Tenga en cuenta que agregaremos componentes adicionales a medida que se publiquen actualizaciones de Visual Studio.

Tenga en cuenta también lo siguiente sobre esta página:

* Cada carga de trabajo tiene su propia sección, seguida por el identificador de la carga de trabajo y una tabla de los componentes que están disponibles para la carga de trabajo.
* De forma predeterminada, los componentes con carácter **Obligatorio** se instalarán cuando se instala la carga de trabajo. Si lo desea, también puede instalar los componentes con la marca **Recomendado** y **Opcional**.
* También hemos agregado una sección que muestra los componentes adicionales que no están asociados a ninguna carga de trabajo.

Para obtener más información acerca de cómo utilizar estos identificadores, vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Y, para obtener una lista de los identificadores de componente y carga de trabajo para otros productos, consulte la página [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (Identificadores de componente y carga de trabajo de Visual Studio 2017).

## <a name="msbuild-tools"></a>Herramientas de MSBuild

**Id.:** Microsoft.VisualStudio.Workload.MSBuildTools

**Descripción:** proporciona las herramientas necesarias para crear aplicaciones basadas en MSBuild.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools Core | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.FSharp.MSBuild | compilador de F# | 15.0.26606.0 | Optional

## <a name="net-core-build-tools"></a>Herramientas de compilación de .NET Core

**Id.:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Descripción:** herramientas para crear aplicaciones de .NET Core.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obligatorio

## <a name="visual-c-build-tools"></a>Herramientas de compilación de Visual C++

**Id.:** Microsoft.VisualStudio.Workload.VCTools

**Descripción:** compile aplicaciones clásicas basadas en Windows con la tecnología del conjunto de herramientas de Visual C++, ATL y características opcionales como MFC y C++/CLI.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Características principales de Visual C++ Build Tools | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Actualización de Visual C++ 2017 Redistributable | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.0.26621.2 | Obligatorio
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.CMake.Project | Herramientas de Visual C++ para CMake | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK de Windows 10 SDK (10.0.15063.0) para escritorio C++ x86 y x64 | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK de Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK de Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de herramientas de VC++ 2015.3 v140 para el escritorio (x86, x64) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Compatibilidad con ATL para Visual C++ | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Compatibilidad con MFC y ATL (x86 y x64) | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimental) | 15.0.26724.1 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Compatibilidad con C++/CLI | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos para biblioteca estándar (experimental) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK de Windows 8.1 y SDK de UCRT | 15.0.26208.0 | Optional

## <a name="web-development-build-tools"></a>Herramientas de compilación de desarrollo web

**Id.:** Microsoft.VisualStudio.Workload.WebBuildTools

**Descripción:** tareas y objetivos de MSBuild para la creación de aplicaciones web.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Herramientas de compilación de desarrollo web | 15.0.26323.1 | Obligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.0.26606.0 | Se recomienda
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.0.26606.0 | Se recomienda
Microsoft.Net.Component.3.5.DeveloperTools | Herramientas de desarrollo para .NET Framework 3.5 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 15.0.26419.1 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 15.0.26606.0 | Optional

## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | Nombre | Versión
--- | --- | ---
no disponible | no disponible | no disponible

## <a name="see-also"></a>Vea también

* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)

