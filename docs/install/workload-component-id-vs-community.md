---
title: Identificadores de componente y carga de trabajo de Visual Studio Community 2017 | Microsoft Docs
description: "Uso de identificadores de componente y carga de trabajo para instalar Visual Studio mediante la línea de comandos o especificarlo como una dependencia en un manifiesto VSIX"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 03/07/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
- vs-ide-sdk
ms.assetid: 58494fc3-12de-4761-bd4a-74b54f72bfb3
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
translationtype: Human Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 9055f1352cce133d853d73d378933ddf8b7e3d78
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-community-2017-workload-and-component-ids"></a>Identificadores de componente y carga de trabajo de Visual Studio Community 2017

Las tablas de esta página presentan los identificadores que puede usar para instalar Visual Studio mediante la línea de comandos o que puede especificar como una dependencia en un manifiesto VSIX. Tenga en cuenta que agregaremos componentes adicionales a medida que se publiquen actualizaciones de Visual Studio.

Tenga en cuenta también lo siguiente sobre la página:

* Cada carga de trabajo tiene su propia sección, seguida por el identificador de la carga de trabajo y una tabla de los componentes que están disponibles para la carga de trabajo.
* De forma predeterminada, los componentes con carácter **Obligatorio** se instalarán cuando se instala la carga de trabajo. Si lo desea, también puede instalar los componentes con la marca **Recomendado** y **Opcional**.
* También hemos agregado una sección que muestra los componentes adicionales que no están asociados a ninguna carga de trabajo.

Al establecer las dependencias del manifiesto de VSIX, debe especificar solo identificadores de componentes. Utilice las tablas de esta página para determinar las dependencias de componente mínimas. En algunos casos, esto podría significar que se especifique solo un componente de una carga de trabajo. En otros escenarios, puede significar que especifique varios componentes de una sola carga de trabajo o varios componentes de varias cargas de trabajo. Para obtener más información, consulte la página [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Migración de proyectos de extensibilidad a Visual Studio 2017).

Para obtener más información acerca de cómo utilizar estos identificadores, vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Y, para obtener una lista de los identificadores de componente y carga de trabajo para otros productos, consulte la página [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (Identificadores de componente y carga de trabajo de Visual Studio 2017).


## <a name="visual-studio-core-editor-included-with-visual-studio-community-2017"></a>Editor de núcleo de Visual Studio (incluido con Visual Studio Community 2017)

**Id.:** Microsoft.VisualStudio.Workload.CoreEditor

**Descripción:** la experiencia del shell principal de Visual Studio, que incluye edición de código compatible con la sintaxis, control de código fuente y administración de elementos de trabajo.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor de núcleo de Visual Studio | Obligatorio


## <a name="azure-development"></a>Desarrollo de Azure

**Id.:** Microsoft.VisualStudio.Workload.Azure

**Descripción:** Azure SDK, herramientas y proyectos de desarrollo de aplicaciones en la nube y creación de recursos.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Obligatorio
Microsoft.Component.NetFX.Core.Runtime | Tiempo de ejecución de .NET Core | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0.1 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | Obligatorio
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | Obligatorio
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Obligatorio
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Requisitos previos del desarrollo de Azure | Obligatorio
Component.WebSocket | WebSocket4Net | Se recomienda
Microsoft.Component.Azure.DataLake.Tools | Herramientas de Azure Data Lake | Se recomienda
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | Se recomienda
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | SDK de Azure Mobile Apps | Se recomienda
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Herramientas principales de Azure Resource Manager | Se recomienda
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Herramientas de Service Fabric | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas de generación de perfiles | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | Se recomienda
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Se recomienda
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | Se recomienda
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | Se recomienda
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | Se recomienda
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Se recomienda
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Se recomienda
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Se recomienda
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | Se recomienda
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Herramientas de Azure Cloud Services | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Herramientas de Azure Resource Manager | Se recomienda
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | Optional
Microsoft.VisualStudio.Component.PowerShell.Tools | Herramientas de PowerShell | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional


## <a name="data-storage-and-processing"></a>Almacenamiento y procesamiento de datos

**Id.:** Microsoft.VisualStudio.Workload.Data

**Descripción:** conecte, desarrolle y pruebe soluciones de datos con SQL Server, Azure Data Lake, Hadoop o Azure ML.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Component.Redgate.ReadyRoll | Redgate ReadyRoll | Se recomienda
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt | Se recomienda
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | Se recomienda
Component.WebSocket | WebSocket4Net | Se recomienda
Microsoft.Component.Azure.DataLake.Tools | Herramientas de Azure Data Lake | Se recomienda
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Se recomienda
Microsoft.Component.MSBuild | MSBuild | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | Se recomienda
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Se recomienda
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | Se recomienda
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | Se recomienda
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | Se recomienda
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | Se recomienda
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Se recomienda
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | Se recomienda
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | Se recomienda
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | Se recomienda
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Se recomienda
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Se recomienda
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Se recomienda
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | Se recomienda
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Se recomienda
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | Optional


## <a name="net-desktop-development"></a>Desarrollo de escritorio de .NET

**Id.:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descripción:**: compile aplicaciones de WPF, Windows Forms y consola mediante .NET Framework.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Obligatorio
Microsoft.Component.MSBuild | MSBuild | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | Obligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Herramientas de desarrollo de escritorio de .NET | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | Obligatorio
Microsoft.ComponentGroup.Blend | Blend para Visual Studio | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas de generación de perfiles | Se recomienda
Microsoft.VisualStudio.Component.EntityFramework | Herramientas de Entity Framework 6 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Se recomienda
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Se recomienda
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Optional
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | Optional
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0.1 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | Optional
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Optional
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | Optional


## <a name="game-development-with-unity"></a>Desarrollo de juegos con Unity

**Id.:** Microsoft.VisualStudio.Workload.ManagedGame

**Descripción:** cree juegos en 2D y 3D con Unity, un entorno de desarrollo multiplataforma muy eficaz.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Obligatorio
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools para Unity | Obligatorio
Component.UnityEngine | Editor de Unity | Se recomienda


## <a name="linux-development-with-c"></a>Desarrollo para Linux con C++

**Id.:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descripción:** cree y depure aplicaciones que se ejecutan en un entorno de Linux.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Component.MDD.Linux | Visual C++ para desarrollo de aplicaciones para Linux | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | Obligatorio


## <a name="desktop-development-with-c"></a>Desarrollo para el escritorio con C++

**Id.:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descripción:** compile aplicaciones clásicas basadas en Windows con la tecnología del conjunto de herramientas de Visual C++, ATL y características opcionales como MFC y C++/CLI.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Obligatorio
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | Obligatorio
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | Obligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | Obligatorio
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | Obligatorio
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Herramientas de arquitectura para C++ | Obligatorio
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Características principales de escritorio para Visual C++ | Obligatorio
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | Se recomienda
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Se recomienda
Microsoft.VisualStudio.Component.VC.CMake.Project | Herramientas de Visual C++ para CMake | Se recomienda
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | Se recomienda
Component.Incredibuild | IncrediBuild | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Optional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de herramientas de VC++ 2015.3 v140 (x86, x64) | Optional
Microsoft.VisualStudio.Component.VC.ATL | Compatibilidad con ATL para Visual C++ | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Compatibilidad con MFC y ATL (x86 y x64) | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimental) | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Compatibilidad con C++/CLI | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos de bibliotecas estándar | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | Optional
Microsoft.VisualStudio.Component.WinXP | Soporte de Windows XP para C++ | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK de Windows 8.1 y SDK de UCRT | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Soporte de Windows XP para C++ | Optional


## <a name="game-development-with-c"></a>Desarrollo de juegos con C++

**Id.:** Microsoft.VisualStudio.Workload.NativeGame

**Descripción:** use toda la capacidad de C++ para crear juegos profesionales con tecnología de DirectX, Unreal o Cocos2d.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | Obligatorio
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | Se recomienda
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Se recomienda
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | Se recomienda
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | Se recomienda
Component.Cocos | Cocos | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.Unreal | Instalador de Unreal Engine | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | Optional
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK de Windows 8.1 y SDK de UCRT | Optional


## <a name="mobile-development-with-c"></a>Desarrollo móvil con C++

**Id.:** Microsoft.VisualStudio.Workload.NativeMobile

**Descripción:** cree aplicaciones multiplataforma para iOS, Android o Windows con C++.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | Obligatorio
Component.Android.NDK.R13B | Android NDK (R13B) | Se recomienda
Component.Android.SDK19 | Instalación de Android SDK (niveles de API 19 y 21) | Se recomienda
Component.Android.SDK22 | Instalación de Android SDK (nivel de API 22) | Se recomienda
Component.Ant | Apache Ant (1.9.3) | Se recomienda
Component.MDD.Android | Herramientas de desarrollo de Android en C ++ | Se recomienda
Component.Android.Emulator | Emulador de Visual Studio para Android | Optional
Component.Android.NDK.R11C | Android NDK (R11C) | Optional
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 bits) | Optional
Component.Android.NDK.R12B | Android NDK (R12B) | Optional
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 bits) | Optional
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 bits) | Optional
Component.Android.SDK23 | Instalación de Android SDK (nivel de API 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Emulador de Android de Google	 (nivel de API 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.JavaJDK | Kit de desarrollo de Java SE (8.0.920.14) | Optional
Component.MDD.IOS | Herramientas de desarrollo de iOS en C++ | Optional


## <a name="net-core-cross-platform-development"></a>Desarrollo multiplataforma de .NET Core

**Id.:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descripción:** compile aplicaciones multiplataforma mediante NET Core, ASP.NET Core, HTML, JavaScript y CSS

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Obligatorio
Microsoft.Component.MSBuild | MSBuild | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0.1 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | Obligatorio
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Obligatorio
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | Se recomienda


## <a name="mobile-development-with-net"></a>Desarrollo móvil con .NET

**Id.:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descripción:** cree aplicaciones multiplataforma para iOS, Android o Windows con Xamarin.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | Obligatorio
Component.Android.NDK.R13B | Android NDK (R13B) | Se recomienda
Component.Android.SDK23 | Instalación de Android SDK (nivel de API 23) | Se recomienda
Component.Google.Android.Emulator.API23.V2 | Emulador de Android de Google	 (nivel de API 23) | Se recomienda
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Se recomienda
Component.JavaJDK | Kit de desarrollo de Java SE (8.0.920.14) | Se recomienda
Component.Xamarin | Xamarin | Se recomienda
Component.Xamarin.Inspector | Xamarin Workbooks | Se recomienda
Component.Xamarin.Profiler | Xamarin Profiler | Se recomienda
Component.Xamarin.RemotedSimulator | Simulador remoto de Xamarin | Se recomienda
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Se recomienda
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas de generación de perfiles | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Optional
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Emulador de Windows 10 Mobile (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Herramientas de la Plataforma universal de Windows para Xamarin (2.0) | Optional


## <a name="aspnet-and-web-development"></a>Desarrollo web y ASP.NET

**Id.:** Microsoft.VisualStudio.Workload.NetWeb

**Descripción:** compile aplicaciones web mediante ASP.NET, ASP.NET Core, HTML, JavaScript y CSS.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Obligatorio
Microsoft.Component.MSBuild | MSBuild | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0.1 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | Obligatorio
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Obligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas de generación de perfiles | Se recomienda
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | Se recomienda
Microsoft.VisualStudio.Component.EntityFramework | Herramientas de Entity Framework 6 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Se recomienda
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Se recomienda
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Se recomienda
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | Optional
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | Optional


## <a name="nodejs-development"></a>Desarrollo de Node.js

**Id.:** Microsoft.VisualStudio.Workload.Node

**Descripción:** cree aplicaciones de red escalables con Node.js, un tiempo de ejecución de JavaScript asincrónico y orientado a eventos.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | Obligatorio
Microsoft.VisualStudio.Component.Node.Tools | Compatibilidad con Node.js | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | Obligatorio
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | Se recomienda
Microsoft.VisualStudio.Component.Git | Git para Windows | Se recomienda
Component.WebSocket | WebSocket4Net | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas de generación de perfiles | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | Optional


## <a name="officesharepoint-development"></a>Desarrollo de Office y SharePoint

**Id.:** Microsoft.VisualStudio.Workload.Office

**Descripción:** cree complementos de Office y SharePoint, soluciones de SharePoint y complementos VSTO mediante C#, VB y JavaScript.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Obligatorio
Microsoft.Component.MSBuild | MSBuild | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | Obligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Herramientas de desarrollo de escritorio de .NET | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Obligatorio
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools para Visual Studio | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | Obligatorio
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | Obligatorio
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Obligatorio
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | Obligatorio
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools para Office (VSTO) | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Optional


## <a name="universal-windows-platform-development"></a>Desarrollo de la Plataforma universal de Windows

**Id.:** Microsoft.VisualStudio.Workload.Universal

**Descripción:** cree aplicaciones para la Plataforma universal de Windows con C#, VB, JavaScript u opcionalmente C++.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Obligatorio
Microsoft.Component.NetFX.Native | .NET Native | Obligatorio
Microsoft.ComponentGroup.Blend | Blend para Visual Studio | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas de generación de perfiles | Obligatorio
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | Obligatorio
Microsoft.VisualStudio.Component.UWP.Support | Herramientas de la Plataforma universal de Windows (2.0) | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Herramientas de la Plataforma universal de Windows para Cordova (2.0) | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Herramientas de la Plataforma universal de Windows para Xamarin (2.0) | Obligatorio
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Se recomienda
Microsoft.Component.VC.Runtime.OSSupport | Tiempo de ejecución de Visual C++ para UWP | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Emulador de Windows 10 Mobile (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Bibliotecas y compiladores de Visual Studio C++ para ARM | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Herramientas de la Plataforma universal de Windows de C++ | Optional


## <a name="visual-studio-extension-development"></a>Desarrollo de extensiones de Visual Studio

**Id.:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descripción:** cree complementos y extensiones para Visual Studio, como nuevos comandos, analizadores de código y ventanas de herramientas.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | Obligatorio
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Requisitos previos para el desarrollo de extensiones de Visual Studio | Obligatorio
Microsoft.VisualStudio.Component.CodeClone | Clon de código | Se recomienda
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | Se recomienda
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas de generación de perfiles | Se recomienda
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Se recomienda
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Se recomienda
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Se recomienda
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | Se recomienda
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Optional
Microsoft.Component.MSBuild | MSBuild | Optional
Microsoft.Component.VC.Runtime.OSSupport | Tiempo de ejecución de Visual C++ para UWP | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | Optional
Microsoft.VisualStudio.Component.DslTools | SDK de modelado | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | Optional
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | Optional
Microsoft.VisualStudio.Component.VC.ATL | Compatibilidad con ATL para Visual C++ | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Compatibilidad con MFC y ATL (x86 y x64) | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | Optional
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | Optional


## <a name="mobile-development-with-javascript"></a>Desarrollo móvil con JavaScript

**Id.:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Descripción:** compile aplicaciones de Android, iOS y UWP con Herramientas para Apache Cordova.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Name | Tipo de dependencia
--- | --- | ---
Component.CordovaToolset.6.3.1 | Conjunto de herramientas de Cordova 6.3.1 | Obligatorio
Component.WebSocket | WebSocket4Net | Obligatorio
Microsoft.VisualStudio.Component.Cordova | Características principales del desarrollo móvil con JavaScript | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | Obligatorio
Component.Android.SDK23 | Instalación de Android SDK (nivel de API 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Emulador de Android de Google	 (nivel de API 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.JavaJDK | Kit de desarrollo de Java SE (8.0.920.14) | Optional
Microsoft.Component.ClickOnce | Publicación de ClickOnce | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas de generación de perfiles | Optional
Microsoft.VisualStudio.Component.Git | Git para Windows | Optional
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Emulador de Windows 10 Mobile (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Herramientas de la Plataforma universal de Windows para Cordova (2.0) | Optional
## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | Name
--- | ---
Component.GitHub.VisualStudio | Extensión de GitHub para Visual Studio
Microsoft.Component.Blend.SDK.WPF | SDK de Blend para Visual Studio para .NET
Microsoft.Component.HelpViewer | Visor de Ayuda
Microsoft.Net.Component.3.5.DeveloperTools | Herramientas de desarrollo para .NET Framework 3.5
Microsoft.VisualStudio.Component.DependencyValidation.Community | Validación de dependencias
Microsoft.VisualStudio.Component.LinqToSql | Herramientas de LINQ to SQL
Microsoft.VisualStudio.Component.TestTools.Core | Características principales de las herramientas de pruebas
Microsoft.VisualStudio.Component.TypeScript.2.0 | SDK de TypeScript 2.0

## <a name="see-also"></a>Vea también

* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)

