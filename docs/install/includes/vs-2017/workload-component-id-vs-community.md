---
title: Identificadores de componente y carga de trabajo de Visual Studio Community 2017
titleSuffix: ''
description: Uso de identificadores de componente y carga de trabajo para instalar Visual Studio mediante la línea de comandos o especificarlo como una dependencia en un manifiesto VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 2/12/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: dbc7fa1f5b931a598a607ce76cfe5c7f336e8ee2
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68177679"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2017"></a>Editor de núcleo de Visual Studio (incluido con Visual Studio Community 2017)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Descripción:** La experiencia del shell principal de Visual Studio, que incluye edición de código compatible con la sintaxis, control de código fuente y administración de elementos de trabajo.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor de núcleo de Visual Studio | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Página principal de Visual Studio para usuarios de C++ | 15.0.27128.1 | Optional

## <a name="azure-development"></a>Desarrollo de Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Descripción:** SDK de Azure, herramientas y proyectos para desarrollar aplicaciones en la nube, crear recursos y compilar contenedores, además de ofrecer compatibilidad con Docker.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Obligatorio
Component.Microsoft.VisualStudio.Web.AzureFunctions | Herramientas de Microsoft Azure WebJobs | 15.7.27617.1 | Obligatorio
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 15.8.27705.0 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Component.NetFX.Core.Runtime | Tiempo de ejecución de .NET Core | 15.0.26208.0 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.9.28307.421 | Obligatorio
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.9.28307.421 | Obligatorio
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.9.28125.51 | Obligatorio
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 15.9.28107.0 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 15.8.27906.1 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Herramientas de desarrollo de contenedor: herramientas de compilación | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Compatibilidad con el lenguaje F# para proyectos web | 15.9.28307.421 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Requisitos previos del desarrollo de Azure | 15.9.28107.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de Microsoft Azure WebJobs | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 15.9.28219.51 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Microsoft.Component.Azure.DataLake.Tools | Herramientas de Azure Data Lake y Stream Analytics | 15.9.28107.0 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.AspNet45 | Características avanzadas de ASP.NET | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | SDK de Azure Mobile Apps | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Herramientas principales de Azure Resource Manager | 15.9.28107.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Herramientas de Service Fabric | 15.8.27825.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 15.9.28107.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Herramientas de compilación para Azure Cloud Services | 15.7.27617.1 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Herramientas de Azure Cloud Services | 15.0.26504.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Herramientas de Azure Resource Manager | 15.0.27005.2 | Se recomienda
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | SDK de .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.6.27406.0 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para Web | 15.6.27406.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 2.0 | 15.8.27729.1 | Optional
Microsoft.NetCore.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 2.0 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Optional

## <a name="data-storage-and-processing"></a>Almacenamiento y procesamiento de datos

**ID:** Microsoft.VisualStudio.Workload.Data

**Descripción:** Conecte, desarrolle y pruebe soluciones de datos con SQL Server, Azure Data Lake o Hadoop.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Se recomienda
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 15.8.27705.0 | Se recomienda
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 3.1.7.2062 | Se recomienda
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Se recomienda
Microsoft.Component.Azure.DataLake.Tools | Herramientas de Azure Data Lake y Stream Analytics | 15.9.28107.0 | Se recomienda
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Se recomienda
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Se recomienda
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.9.28307.421 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.9.28307.421 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.9.28125.51 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 15.9.28107.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Herramientas de compilación para Azure Cloud Services | 15.7.27617.1 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 15.9.28107.0 | Se recomienda
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 15.8.27906.1 | Se recomienda
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Herramientas de desarrollo de contenedor: herramientas de compilación | 15.7.27617.1 | Se recomienda
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Se recomienda
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Se recomienda
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.8.27825.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 15.9.28219.51 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Se recomienda
Microsoft.VisualStudio.Component.FSharp.Desktop | Compatibilidad con el lenguaje de escritorio F# | 15.8.27825.0 | Optional

## <a name="data-science-and-analytical-applications"></a>Aplicaciones analíticas y de ciencia de datos

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Descripción:** Lenguajes y herramientas para crear aplicaciones de ciencia de datos, incluidos Python, R y F#.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Anaconda3.x64 | Anaconda3 64 bits (5.2.0) | 5.2.0 | Se recomienda
Microsoft.Component.CookiecutterTools | Compatibilidad con plantillas de Cookiecutter | 15.0.26621.2 | Se recomienda
Microsoft.Component.PythonTools | Compatibilidad con el lenguaje Python | 15.0.26823.1 | Se recomienda
Microsoft.Component.PythonTools.Web | Compatibilidad web con Python | 15.9.28107.0 | Se recomienda
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 15.9.28107.0 | Se recomienda
Microsoft.VisualStudio.Component.FSharp.Desktop | Compatibilidad con el lenguaje de escritorio F# | 15.8.27825.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Se recomienda
Microsoft.VisualStudio.Component.R.Open | Cliente de Microsoft R (3.3.2) | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.RHost | Compatibilidad del entorno de tiempo de ejecución con herramientas de desarrollo de R | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.RTools | Compatibilidad con el lenguaje R | 15.0.26919.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Se recomienda
Component.Anaconda2.x64 | Anaconda2 64 bits (5.2.0) | 5.2.0 | Optional
Component.Anaconda2.x86 | Anaconda2 32 bits (5.2.0) | 5.2.0 | Optional
Component.Anaconda3.x86 | Anaconda3 32 bits (5.2.0) | 5.2.0 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.6.27309.0 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Herramientas de desarrollo nativo de Python | 15.9.28307.102 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de herramientas de VC++ 2015.3 v14.00 (v140) para escritorio | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 15.9.28307.102 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.6.27406.0 | Optional

## <a name="net-desktop-development"></a>Desarrollo de escritorio de .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descripción:** Compile aplicaciones WPF, Windows Forms y de consola con C#, Visual Basic y F#.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Herramientas de desarrollo de escritorio de .NET | 15.7.27625.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Obligatorio
Microsoft.ComponentGroup.Blend | Blend para Visual Studio | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 15.0.27005.2 | Se recomienda
Microsoft.VisualStudio.Component.EntityFramework | Herramientas de Entity Framework 6 | 15.6.27406.0 | Se recomienda
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Optional
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 15.8.27705.0 | Optional
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | SDK de .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 2.0 | 15.8.27729.1 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 15.8.27906.1 | Optional
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Herramientas de desarrollo de contenedor: herramientas de compilación | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | Compatibilidad con el lenguaje de escritorio F# | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Optional
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Optional
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 15.9.28219.51 | Optional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Optional

## <a name="game-development-with-unity"></a>Desarrollo de juegos con Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Descripción:** Cree juegos en 2D y 3D con Unity, un entorno de desarrollo multiplataforma muy eficaz.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Herramientas de desarrollo para .NET Framework 3.5 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools para Unity | 15.7.27617.1 | Obligatorio
Component.UnityEngine.x64 | Editor Unity 2018.3 de 64 bits | 15.9.28307.271 | Se recomienda
Component.UnityEngine.x86 | Editor Unity 5.6 de 32 bits | 15.6.27406.0 | Se recomienda

## <a name="linux-development-with-c"></a>Desarrollo para Linux con C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descripción:** Cree y depure aplicaciones que se ejecutan en un entorno de Linux.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.MDD.Linux | Visual C++ para desarrollo de aplicaciones para Linux | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.6.27406.0 | Obligatorio
Component.Linux.CMake | Herramientas de Visual C++ para CMake y Linux | 15.9.28307.102 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 15.9.28307.102 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Se recomienda
Component.MDD.Linux.GCC.arm | Desarrollo incrustado e IoT | 15.6.27309.0 | Optional

## <a name="desktop-development-with-c"></a>Desarrollo para el escritorio con C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descripción:** Compile aplicaciones de escritorio de Windows con el conjunto de herramientas de Microsoft C++, ATL o MFC.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Actualización de Visual C++ 2017 Redistributable | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Características principales de escritorio para Visual C++ | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 15.0.27005.2 | Se recomienda
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.ATL | ATL de Visual C++ para x86 y x64 | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.CMake.Project | Herramientas de Visual C++ para CMake | 15.9.28307.102 | Se recomienda
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Test Adapter para Boost.Test | 15.8.27906.1 | Se recomienda
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter para Google Test | 15.8.27906.1 | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 15.9.28307.102 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Se recomienda
Component.Incredibuild | IncrediBuild: Aceleración de compilación | 15.7.27617.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de herramientas de VC++ 2015.3 v14.00 (v140) para escritorio | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC de Visual C++ para x86 y x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Compatibilidad con C++/CLI | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos para biblioteca estándar (experimental) | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK de Windows 10 (10.0.15063.0) para escritorio C++ [x86 y x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK de Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK de Windows 10 (10.0.15063.0) para UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK de Windows 10 (10.0.16299.0) para escritorio C++ [x86 and x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | SDK de Windows 10 SDK (10.0.16299.0) para escritorio C++ [ARM y ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK de Windows 10 (10.0.17134.0) | 15.9.28307.102 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.WinXP | Soporte de Windows XP para C++ | 15.8.27924.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK de Windows 8.1 y SDK de UCRT | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Soporte de Windows XP para C++ | 15.8.27705.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | SDK de Windows 10 (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | SDK de Windows 10 (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="game-development-with-c"></a>Desarrollo de juegos con C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Descripción:** Use toda la capacidad de C++ para crear juegos profesionales con tecnología de DirectX, Unreal o Cocos2d.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Actualización de Visual C++ 2017 Redistributable | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 15.9.28307.102 | Se recomienda
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | Optional
Component.Android.SDK23.Private | Instalación de Android SDK (nivel de API 23) (instalación local para desarrollo móvil con JavaScript o C++) | 15.9.28016.0 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Optional
Component.Cocos | Cocos | 15.0.26906.1 | Optional
Component.Incredibuild | IncrediBuild: Aceleración de compilación | 15.7.27617.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional
Component.MDD.Android | Herramientas de desarrollo de Android en C ++ | 15.0.26606.0 | Optional
Component.OpenJDK | Distribución de Microsoft OpenJDK | 15.9.28125.51 | Optional
Component.Unreal | Instalador de Unreal Engine | 15.8.27729.1 | Optional
Component.Unreal.Android | Compatibilidad de Visual Studio con Android para Unreal Engine | 15.9.28307.341 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 15.9.28016.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK de Windows 10 (10.0.15063.0) para escritorio C++ [x86 y x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK de Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK de Windows 10 (10.0.15063.0) para UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK de Windows 10 (10.0.16299.0) para escritorio C++ [x86 and x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | SDK de Windows 10 SDK (10.0.16299.0) para escritorio C++ [ARM y ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK de Windows 10 (10.0.17134.0) | 15.9.28307.102 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK de Windows 8.1 y SDK de UCRT | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | SDK de Windows 10 (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | SDK de Windows 10 (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="mobile-development-with-c"></a>Desarrollo móvil con C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Descripción:** Compile aplicaciones multiplataforma para iOS, Android o Windows con C++.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Android.SDK19.Private | Instalación de Android SDK (nivel de API 19) (instalación local para desarrollo móvil con JavaScript o C++) | 15.9.28107.0 | Obligatorio
Component.Android.SDK21.Private | Instalación de Android SDK (nivel de API 21) (instalación local para desarrollo móvil con JavaScript o C++) | 15.9.28016.0 | Obligatorio
Component.Android.SDK22.Private | Instalación de Android SDK (nivel de API 22) (instalación local para desarrollo móvil con JavaScript o C++) | 15.9.28016.0 | Obligatorio
Component.Android.SDK23.Private | Instalación de Android SDK (nivel de API 23) (instalación local para desarrollo móvil con JavaScript o C++) | 15.9.28016.0 | Obligatorio
Component.Android.SDK25.Private | Instalación de Android SDK (nivel de API 25) (instalación local para desarrollo móvil con JavaScript o C++) | 15.9.28016.0 | Obligatorio
Component.OpenJDK | Distribución de Microsoft OpenJDK | 15.9.28125.51 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.6.27406.0 | Obligatorio
Component.Android.NDK.R15C | Android NDK (R15C) | 15.2.1 | Se recomienda
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Se recomienda
Component.MDD.Android | Herramientas de desarrollo de Android en C ++ | 15.0.26606.0 | Se recomienda
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | Optional
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 bits) | 12.1.11 | Optional
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.7 | Optional
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 bits) | 13.1.8 | Optional
Component.Android.NDK.R15C_3264 | Android NDK (R15C) (32bits) | 15.2.1 | Optional
Component.Google.Android.Emulator.API23.Private | Google Android Emulator (nivel de API 23) (instalación local) | 15.6.27413.0 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (instalación local) | 15.9.28307.421 | Optional
Component.Incredibuild | IncrediBuild: Aceleración de compilación | 15.7.27617.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional
Component.MDD.IOS | Herramientas de desarrollo de iOS en C++ | 15.0.26621.2 | Optional

## <a name="net-core-cross-platform-development"></a>Desarrollo multiplataforma de .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descripción:** Compile aplicaciones multiplataforma con .NET Core, ASP.NET Core, HTML/JavaScript y Containers, además de ofrecer compatibilidad con Docker.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Obligatorio
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 15.8.27705.0 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 15.9.28107.0 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 15.8.27906.1 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Herramientas de desarrollo de contenedor: herramientas de compilación | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Compatibilidad con el lenguaje F# para proyectos web | 15.9.28307.421 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 15.9.28219.51 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Component.Microsoft.VisualStudio.Web.AzureFunctions | Herramientas de Microsoft Azure WebJobs | 15.7.27617.1 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.8.27825.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.9.28307.421 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.9.28307.421 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.9.28125.51 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.8.27825.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de Microsoft Azure WebJobs | 15.7.27617.1 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Herramientas en la nube para el desarrollo web | 15.8.27729.1 | Se recomienda
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.6.27406.0 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para Web | 15.6.27406.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 2.0 | 15.8.27729.1 | Optional
Microsoft.NetCore.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 2.0 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Compatibilidad con IIS en tiempo de desarrollo | 15.9.28219.51 | Optional

## <a name="mobile-development-with-net"></a>Desarrollo móvil con .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descripción:** Compile aplicaciones multiplataforma para iOS, Android o Windows con Xamarin.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Xamarin | Xamarin | 15.8.27906.1 | Obligatorio
Component.Xamarin.RemotedSimulator | Simulador remoto de Xamarin | 15.6.27323.2 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 2.0 | 15.6.27406.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 2.0 | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.Merq | Herramientas internas comunes de Xamarin | 15.8.27924.0 | Obligatorio
Microsoft.VisualStudio.Component.MonoDebugger | Depurador de Mono | 15.0.26720.2 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Motor de plantillas de ASP.NET | 15.8.27729.1 | Obligatorio
Component.Android.SDK27 | Instalación de Android SDK (nivel de API 27) | 15.9.28016.0 | Se recomienda
Component.Google.Android.Emulator.API27 | Google Android Emulator (nivel de API 27) | 15.9.28307.421 | Se recomienda
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (instalación global) | 15.9.28307.421 | Se recomienda
Component.OpenJDK | Distribución de Microsoft OpenJDK | 15.9.28125.51 | Se recomienda
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26606.0 | Optional
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Optional
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 15.9.28307.102 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Herramientas de la Plataforma universal de Windows para Xamarin | 15.9.28307.102 | Optional

## <a name="aspnet-and-web-development"></a>Desarrollo web y ASP.NET

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Descripción:** Compile aplicaciones web con ASP.NET, ASP.NET Core, HTML/JavaScript y Containers, además de ofrecer compatibilidad con Docker.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Obligatorio
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 15.8.27705.0 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 15.9.28107.0 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 15.8.27906.1 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Herramientas de desarrollo de contenedor: herramientas de compilación | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Compatibilidad con el lenguaje F# para proyectos web | 15.9.28307.421 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 15.9.28219.51 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Component.Microsoft.VisualStudio.Web.AzureFunctions | Herramientas de Microsoft Azure WebJobs | 15.7.27617.1 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.8.27825.0 | Se recomienda
Microsoft.VisualStudio.Component.AspNet45 | Características avanzadas de ASP.NET | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.9.28307.421 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.9.28307.421 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.9.28125.51 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.EntityFramework | Herramientas de Entity Framework 6 | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de Microsoft Azure WebJobs | 15.7.27617.1 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Herramientas en la nube para el desarrollo web | 15.8.27729.1 | Se recomienda
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | SDK de .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.6.27406.0 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para Web | 15.6.27406.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 2.0 | 15.8.27729.1 | Optional
Microsoft.NetCore.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 2.0 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Compatibilidad con IIS en tiempo de desarrollo | 15.9.28219.51 | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | Optional

## <a name="nodejs-development"></a>Desarrollo de Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Descripción:** Compile aplicaciones de red escalables con Node.js, un runtime de JavaScript controlado por eventos asincrónicos. 

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Obligatorio
Microsoft.VisualStudio.Component.Node.Build | Soporte de MSBuild para Node.js | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.Node.Tools | Soporte para el desarrollo de Node.js | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.TestTools.Core | Características principales de las herramientas de pruebas | 15.7.27520.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Optional

## <a name="officesharepoint-development"></a>Desarrollo de Office y SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Descripción:** Cree complementos de Office y SharePoint, soluciones de SharePoint y complementos de VSTO mediante C#, VB y JavaScript.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Obligatorio
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 15.8.27705.0 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 15.9.28107.0 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 15.8.27906.1 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Herramientas de desarrollo de contenedor: herramientas de compilación | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Herramientas de desarrollo de escritorio de .NET | 15.7.27625.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools para Visual Studio | 15.8.27924.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 15.9.28219.51 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools para Office (VSTO) | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Se recomienda
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | SDK de .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 15.6.27406.0 | Optional

## <a name="python-development"></a>Desarrollo de Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Descripción:** Edición, depuración, desarrollo interactivo y control de código fuente para Python.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.PythonTools | Compatibilidad con el lenguaje Python | 15.0.26823.1 | Obligatorio
Component.CPython3.x64 | Python 3 64 bits (3.6.6) | 3.6.6 | Se recomienda
Microsoft.Component.CookiecutterTools | Compatibilidad con plantillas de Cookiecutter | 15.0.26621.2 | Se recomienda
Microsoft.Component.PythonTools.Web | Compatibilidad web con Python | 15.9.28107.0 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 15.9.28107.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Se recomienda
Component.Anaconda2.x64 | Anaconda2 64 bits (5.2.0) | 5.2.0 | Optional
Component.Anaconda2.x86 | Anaconda2 32 bits (5.2.0) | 5.2.0 | Optional
Component.Anaconda3.x64 | Anaconda3 64 bits (5.2.0) | 5.2.0 | Optional
Component.Anaconda3.x86 | Anaconda3 32 bits (5.2.0) | 5.2.0 | Optional
Component.CPython2.x64 | Python 2 64 bits (2.7.14) | 2.7.14 | Optional
Component.CPython2.x86 | Python 2 32 bits (2.7.14) | 2.7.14 | Optional
Component.CPython3.x86 | Python 3 32 bits (3.6.6) | 3.6.6 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Optional
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 15.8.27705.0 | Optional
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Optional
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Optional
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Optional
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Optional
Microsoft.Component.PythonTools.UWP | Compatibilidad con IoT de Python | 15.0.26606.0 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.6.27309.0 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Herramientas de desarrollo nativo de Python | 15.9.28307.102 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Optional
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.9.28307.421 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.9.28307.421 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.9.28125.51 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Herramientas de compilación para Azure Cloud Services | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 15.8.27906.1 | Optional
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Herramientas de desarrollo de contenedor: herramientas de compilación | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de herramientas de VC++ 2015.3 v14.00 (v140) para escritorio | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 15.9.28307.102 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 15.9.28219.51 | Optional

## <a name="universal-windows-platform-development"></a>Desarrollo de la Plataforma universal de Windows

**ID:** Microsoft.VisualStudio.Workload.Universal

**Descripción:** Cree aplicaciones para la Plataforma universal de Windows con C#, VB, JavaScript y, opcionalmente, C++.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Obligatorio
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Obligatorio
Microsoft.ComponentGroup.Blend | Blend para Visual Studio | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio
Microsoft.VisualStudio.Component.UWP.Support | Herramientas de la Plataforma universal de Windows | 15.9.28119.51 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 15.9.28307.102 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Herramientas de la Plataforma universal de Windows para Cordova | 15.9.28307.102 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native y .NET Standard | 15.8.27906.1 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Herramientas de la Plataforma universal de Windows para Xamarin | 15.9.28307.102 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Microsoft.Component.VC.Runtime.OSSupport | Tiempo de ejecución de Visual C++ para UWP | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Emulador de Windows 10 Mobile (Fall Creators Update) | 15.0.27406.0 | Optional
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Herramientas de la Plataforma universal de Windows C++ para ARM64 | 15.0.28125.51 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Bibliotecas y compiladores de Visual Studio C++ para ARM | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Bibliotecas y compiladores de Visual C++ para ARM64 | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK de Windows 10 (10.0.15063.0) para escritorio C++ [x86 y x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK de Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK de Windows 10 (10.0.15063.0) para UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK de Windows 10 (10.0.16299.0) para escritorio C++ [x86 and x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | SDK de Windows 10 SDK (10.0.16299.0) para escritorio C++ [ARM y ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK de Windows 10 (10.0.17134.0) | 15.9.28307.102 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Conectividad del dispositivo USB | 15.9.28307.102 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Herramientas de la Plataforma universal de Windows de C++ | 15.9.28307.102 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | SDK de Windows 10 (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | SDK de Windows 10 (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="visual-studio-extension-development"></a>Desarrollo de extensiones de Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descripción:** Cree complementos y extensiones para Visual Studio, incluidos nuevos comandos, analizadores de código y ventanas de herramientas.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Requisitos previos para el desarrollo de extensiones de Visual Studio | 15.7.27625.0 | Obligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Se recomienda
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Component.CodeAnalysis.SDK | SDK de la plataforma del compilador de .NET | 15.0.27729.1 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Tiempo de ejecución de Visual C++ para UWP | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DslTools | SDK de modelado | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.VC.ATL | ATL de Visual C++ para x86 y x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC de Visual C++ para x86 y x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Optional

## <a name="mobile-development-with-javascript"></a>Desarrollo móvil con JavaScript

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Descripción:** Compile aplicaciones para Android, iOS y UWP con Herramientas para Apache Cordova.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Conjunto de herramientas de Cordova 6.3.1 | 15.7.27625.0 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Cordova | Características principales del desarrollo móvil con JavaScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript Project System y herramientas compartidas | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.9.28125.51 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.8.27825.0 | Obligatorio
Component.Android.SDK23.Private | Instalación de Android SDK (nivel de API 23) (instalación local para desarrollo móvil con JavaScript o C++) | 15.9.28016.0 | Optional
Component.Google.Android.Emulator.API23.Private | Google Android Emulator (nivel de API 23) (instalación local) | 15.6.27413.0 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (instalación local) | 15.9.28307.421 | Optional
Component.OpenJDK | Distribución de Microsoft OpenJDK | 15.9.28125.51 | Optional
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.8.27825.0 | Optional
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.Git | Git para Windows | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Emulador de Windows 10 Mobile (Fall Creators Update) | 15.0.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 15.9.28307.102 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Herramientas de la Plataforma universal de Windows para Cordova | 15.9.28307.102 | Optional

## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | nombre | Versión
--- | --- | ---
Component.Android.Emulator | Emulador de Visual Studio para Android | 15.6.27413.0
Component.Android.NDK.R11C | Android NDK (R11C) | 11.3.14
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 bits) | 11.3.16
Component.Android.SDK23 | Instalación de Android SDK (nivel de API 23) (instalación global) | 15.9.28107.0
Component.Android.SDK25 | Instalación de Android SDK (nivel de API 25) | 15.9.28107.0
Component.GitHub.VisualStudio | Extensión de GitHub para Visual Studio | 2.5.2.2500
Component.Google.Android.Emulator.API23.V2 | Google Android Emulator (nivel de API 23) (instalación global) | 15.6.27413.0
Component.Google.Android.Emulator.API25 | Google Android Emulator (nivel de API 25) | 15.7.27604.0
Microsoft.Component.Blend.SDK.WPF | SDK de Blend para Visual Studio para .NET | 15.6.27406.0
Microsoft.Component.HelpViewer | Visor de Ayuda | 15.9.28307.421
Microsoft.VisualStudio.Component.DependencyValidation.Community | Validación de dependencias | 15.0.26208.0
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.27005.2
Microsoft.VisualStudio.Component.LinqToSql | Herramientas de LINQ to SQL | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator | Emulador de Windows 10 Mobile (Anniversary Edition) | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulador de Windows 10 Mobile (Creators Update) | 15.6.27406.0
Microsoft.VisualStudio.Component.Runtime.Node.x86.6.4.0 | Tiempo de ejecución para componentes basados en Node.js v6.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.Runtime.Node.x86.7.4.0 | Tiempo de ejecución para componentes basados en Node.js v7.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.TypeScript.2.0 | SDK de TypeScript 2.0 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | SDK de TypeScript 2.2 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | SDK de TypeScript 2.5 | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | SDK de TypeScript 2.6 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | SDK de TypeScript 2.7 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | SDK de TypeScript 2.8 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | SDK de TypeScript 2.9 | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | SDK de TypeScript 3.0 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | ATL de Visual C++ para ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | ATL de Visual C++ para ARM con mitigaciones de Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | ATL de Visual C++ para ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | ATL de Visual C++ para ARM64 con mitigaciones de Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | ATL de Visual C++ (x86/x64) con mitigaciones de Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | MFC de Visual C++ para x86/x64 con mitigaciones de Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimental) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | MFC de Visual C++ para ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | MFC de Visual C++ para ARM con mitigaciones de Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | MFC de Visual C++ para ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Compatibilidad de MFC de Visual C++ para ARM64 con mitigaciones de Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | Bibliotecas de VC++ 2017 versión 15.9 v14.16 para Spectre (ARM) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | Bibliotecas de VC++ 2017 versión 15.9 v14.16 para Spectre (ARM64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | Bibliotecas de VC++ 2017 versión 15.9 v14.16 para Spectre (x86 y x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Conjunto de herramientas para VC++ 2017 versión 15.4 v14.11 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Conjunto de herramientas para VC++ 2017 versión 15.5 v14.12 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | Conjunto de herramientas para VC++ 2017 versión 15.6 v14.13 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | Conjunto de herramientas para VC++ 2017 versión 15.7 v14.14 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | Conjunto de herramientas de VC++ 2017 versión 15.8 v14.15 | 15.0.28230.55
