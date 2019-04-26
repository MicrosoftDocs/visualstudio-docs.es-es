---
title: Identificadores de componente y carga de trabajo de Visual Studio Enterprise 2019
titleSuffix: ''
description: Uso de identificadores de componente y carga de trabajo para instalar Visual Studio mediante la línea de comandos o especificarlo como una dependencia en un manifiesto VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 04/02/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 5c004b1db829f50b2fed435ad0202308ef3726c8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968404"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Editor principal de Visual Studio (incluido con Visual Studio Enterprise 2019)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Descripción:** La experiencia del shell principal de Visual Studio, que incluye edición de código compatible con la sintaxis, control de código fuente y administración de elementos de trabajo.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor de núcleo de Visual Studio | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Página principal de Visual Studio para usuarios de C++ | 16.0.28315.86 | Optional

## <a name="azure-development"></a>Desarrollo de Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Descripción:** SDK de Azure, herramientas y proyectos para desarrollar aplicaciones en la nube, crear recursos y compilar contenedores, además de ofrecer compatibilidad con Docker.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 16.0.28714.129 | Obligatorio
Component.Microsoft.VisualStudio.Web.AzureFunctions | Herramientas de Azure WebJobs | 16.0.28714.129 | Obligatorio
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 16.0.28315.86 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28516.191 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 16.0.28720.110 | Obligatorio
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Compatibilidad con el lenguaje F# para proyectos web | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.MSODBC.SQL | Controlador ODBC de SQL Server | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilidades de la línea de comandos de SQL Server | 16.0.28707.177 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Requisitos previos del desarrollo de Azure | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de Azure WebJobs | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Microsoft.Component.Azure.DataLake.Tools | Herramientas de Azure Data Lake y Stream Analytics | 16.0.28720.110 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 16.0.28517.75 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 16.0.28516.191 | Se recomienda
Microsoft.VisualStudio.Component.AspNet45 | Características avanzadas de ASP.NET | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools para Kubernetes | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Herramientas principales de Azure Resource Manager | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Herramientas de Service Fabric | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Herramientas de compilación para Azure Cloud Services | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Debugger.Snapshot | Depurador de instantáneas | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Depurador de viaje en el tiempo | 16.0.28714.129 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Herramientas de Azure Cloud Services | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Herramientas de Azure Resource Manager | 16.0.28528.71 | Se recomienda
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | SDK de .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional

## <a name="data-storage-and-processing"></a>Almacenamiento y procesamiento de datos

**ID:** Microsoft.VisualStudio.Workload.Data

**Descripción:** Conecte, desarrolle y pruebe soluciones de datos con SQL Server, Azure Data Lake o Hadoop.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 16.0.28714.129 | Se recomienda
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 16.0.28315.86 | Se recomienda
Microsoft.Component.Azure.DataLake.Tools | Herramientas de Azure Data Lake y Stream Analytics | 16.0.28720.110 | Se recomienda
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 16.0.28517.75 | Se recomienda
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 16.0.28516.191 | Se recomienda
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 16.0.28720.110 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Herramientas de compilación para Azure Cloud Services | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 16.0.28621.142 | Se recomienda
Microsoft.VisualStudio.Component.MSODBC.SQL | Controlador ODBC de SQL Server | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilidades de la línea de comandos de SQL Server | 16.0.28707.177 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 16.0.28621.142 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Se recomienda
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | Compatibilidad con el lenguaje de escritorio F# | 16.0.28315.86 | Optional

## <a name="data-science-and-analytical-applications"></a>Aplicaciones analíticas y de ciencia de datos

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Descripción:** Lenguajes y herramientas para crear aplicaciones de ciencia de datos, como Python y F#.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.PythonTools | Compatibilidad con el lenguaje Python | 16.0.28625.61 | Se recomienda
Microsoft.Component.PythonTools.Minicondax64 | Miniconda de Python | 16.0.28625.61 | Se recomienda
Microsoft.Component.PythonTools.Web | Compatibilidad web con Python | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.FSharp.Desktop | Compatibilidad con el lenguaje de escritorio F# | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Se recomienda
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 16.0.28625.61 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Herramientas de desarrollo nativo de Python | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ Build Tools (v14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++ Build Tools para x64/x86 (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 16.0.28517.75 | Optional

## <a name="net-desktop-development"></a>Desarrollo de escritorio de .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descripción:** Compile aplicaciones WPF, Windows Forms y de consola con C#, Visual Basic y F#.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Herramientas de desarrollo de escritorio de .NET | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Obligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Se recomienda
Microsoft.ComponentGroup.Blend | Blend para Visual Studio | 16.0.28315.86 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 16.0.28517.75 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 16.0.28516.191 | Se recomienda
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.EntityFramework | Herramientas de Entity Framework 6 | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.0.28315.86 | Se recomienda
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 16.0.28315.86 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | SDK de .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | Compatibilidad con el lenguaje de escritorio F# | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | Controlador ODBC de SQL Server | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilidades de la línea de comandos de SQL Server | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 16.0.28517.75 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Optional

## <a name="game-development-with-unity"></a>Desarrollo de juegos con Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Descripción:** Cree juegos en 2D y 3D con Unity, un entorno de desarrollo multiplataforma muy eficaz.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Herramientas de desarrollo para .NET Framework 3.5 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools para Unity | 16.0.28315.86 | Obligatorio
Component.UnityEngine.x64 | Editor Unity 2018.3 de 64 bits | 16.0.28707.178 | Se recomienda
Component.UnityEngine.x86 | Editor Unity 5.6 de 32 bits | 16.0.28707.178 | Se recomienda

## <a name="linux-development-with-c"></a>Desarrollo para Linux con C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descripción:** Cree y depure aplicaciones que se ejecutan en un entorno de Linux.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.MDD.Linux | C++ for Linux Development | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de C++ | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 16.0.28315.86 | Obligatorio
Component.Linux.CMake | Herramientas de CMake en C++ para Linux | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++ Build Tools para x64/x86 (v14.20) | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Se recomienda
Component.MDD.Linux.GCC.arm | Herramientas de desarrollo insertadas e IoT | 16.0.28625.61 | Optional

## <a name="desktop-development-with-c"></a>Desarrollo para el escritorio con C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descripción:** Compile aplicaciones de escritorio de Windows con el conjunto de herramientas de Microsoft C++, ATL o MFC.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | 16.0.28528.71 | Obligatorio
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de C++ | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Actualización de C++ 2019 Redistributable | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Herramientas de arquitectura para C++ | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Características principales de escritorio para Visual C++ | 16.0.28315.86 | Obligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Se recomienda
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.VC.ATL | Herramientas de compilación de ATL de C++ para v142 (x86 y x64) | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.VC.CMake.Project | Herramientas de CMake en C++ para Windows | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Test Adapter para Boost.Test | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter para Google Test | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++ Build Tools para x64/x86 (v14.20) | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Se recomienda
Component.Incredibuild | IncrediBuild: Aceleración de compilación | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ Build Tools (v14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Herramientas de compilación MFC de C++ para v142 (x86 y x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Compatibilidad con C++/CLI para las herramientas de compilación de v142 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos de C++ para las herramientas de compilación de v142 (x64/x86: experimental) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 – VS 2017 C++ Build Tools para x64/x86 (v14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | SDK de Windows 10 (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK de Windows 10 (10.0.17134.0) | 16.0.28517.75 | Optional

## <a name="game-development-with-c"></a>Desarrollo de juegos con C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Descripción:** Use toda la capacidad de C++ para crear juegos profesionales con tecnología de DirectX, Unreal o Cocos2d.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de C++ | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Actualización de C++ 2019 Redistributable | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++ Build Tools para x64/x86 (v14.20) | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 16.0.28517.75 | Se recomienda
Component.Android.NDK.R16B | Android NDK (R16B) | 16.0.28728.38 | Optional
Component.Android.SDK25.Private | Programa de instalación de Android SDK (nivel de API 25) (instalación local para desarrollo móvil con C++) | 16.0.28625.61 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Optional
Component.Cocos | Cocos | 16.0.28315.86 | Optional
Component.Incredibuild | IncrediBuild: Aceleración de compilación | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Component.MDD.Android | Herramientas de desarrollo de Android en C ++ | 16.0.28517.75 | Optional
Component.OpenJDK | OpenJDK (distribución de Microsoft) | 16.0.28625.61 | Optional
Component.Unreal | Instalador de Unreal Engine | 16.0.28625.61 | Optional
Component.Unreal.Android | Compatibilidad con IDE de Android para Unreal Engine | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | SDK de Windows 10 (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK de Windows 10 (10.0.17134.0) | 16.0.28517.75 | Optional

## <a name="mobile-development-with-c"></a>Desarrollo móvil con C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Descripción:** Compile aplicaciones multiplataforma para iOS, Android o Windows con C++.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Android.SDK25.Private | Programa de instalación de Android SDK (nivel de API 25) (instalación local para desarrollo móvil con C++) | 16.0.28625.61 | Obligatorio
Component.OpenJDK | OpenJDK (distribución de Microsoft) | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de C++ | 16.0.28625.61 | Obligatorio
Component.Android.NDK.R16B | Android NDK (R16B) | 16.0.28728.38 | Se recomienda
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Se recomienda
Component.MDD.Android | Herramientas de desarrollo de Android en C ++ | 16.0.28517.75 | Se recomienda
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32 bits) | 16.0.28728.38 | Optional
Component.Google.Android.Emulator.API25.Private | Google Android Emulator (nivel de API 25) (instalación local) | 16.0.28625.61 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (instalación local) | 16.0.28528.71 | Optional
Component.Incredibuild | IncrediBuild: Aceleración de compilación | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Component.MDD.IOS | Herramientas de desarrollo de iOS en C++ | 16.0.28517.75 | Optional

## <a name="net-core-cross-platform-development"></a>Desarrollo multiplataforma de .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descripción:** Compile aplicaciones multiplataforma con .NET Core, ASP.NET Core, HTML/JavaScript y Containers, además de ofrecer compatibilidad con Docker.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 16.0.28714.129 | Obligatorio
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 16.0.28315.86 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28516.191 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Compatibilidad con el lenguaje F# para proyectos web | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.MSODBC.SQL | Controlador ODBC de SQL Server | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilidades de la línea de comandos de SQL Server | 16.0.28707.177 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Se recomienda
Component.Microsoft.VisualStudio.Web.AzureFunctions | Herramientas de Azure WebJobs | 16.0.28714.129 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 16.0.28720.110 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Debugger.Snapshot | Depurador de instantáneas | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Depurador de viaje en el tiempo | 16.0.28714.129 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de Azure WebJobs | 16.0.28621.142 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Herramientas en la nube para el desarrollo web | 16.0.28621.142 | Se recomienda
Microsoft.Net.Core.Component.SDK.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Compatibilidad con IIS en tiempo de desarrollo | 16.0.28315.86 | Optional

## <a name="mobile-development-with-net"></a>Desarrollo móvil con .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descripción:** Compile aplicaciones multiplataforma para iOS, Android o Windows con Xamarin.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Xamarin | Xamarin | 16.0.28625.61 | Obligatorio
Component.Xamarin.RemotedSimulator | Simulador remoto de Xamarin | 16.0.28315.86 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28516.191 | Obligatorio
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.Merq | Herramientas internas comunes de Xamarin | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.MonoDebugger | Depurador de Mono | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Motor de plantillas de ASP.NET | 16.0.28315.86 | Obligatorio
Component.Android.SDK27 | Instalación de Android SDK (nivel de API 27) | 16.0.28517.75 | Se recomienda
Component.OpenJDK | OpenJDK (distribución de Microsoft) | 16.0.28625.61 | Se recomienda

## <a name="aspnet-and-web-development"></a>Desarrollo web y ASP.NET

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Descripción:** Compile aplicaciones web con ASP.NET, ASP.NET Core, HTML/JavaScript y Containers, además de ofrecer compatibilidad con Docker.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 16.0.28714.129 | Obligatorio
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 16.0.28315.86 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28516.191 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Compatibilidad con el lenguaje F# para proyectos web | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.MSODBC.SQL | Controlador ODBC de SQL Server | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilidades de la línea de comandos de SQL Server | 16.0.28707.177 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Se recomienda
Component.Microsoft.VisualStudio.Web.AzureFunctions | Herramientas de Azure WebJobs | 16.0.28714.129 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 16.0.28517.75 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 16.0.28516.191 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.AspNet45 | Características avanzadas de ASP.NET | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 16.0.28720.110 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Debugger.Snapshot | Depurador de instantáneas | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Depurador de viaje en el tiempo | 16.0.28714.129 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.EntityFramework | Herramientas de Entity Framework 6 | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de Azure WebJobs | 16.0.28621.142 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Herramientas en la nube para el desarrollo web | 16.0.28621.142 | Se recomienda
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | SDK de .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Herramientas de desarrollo de .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Herramientas de rendimiento web y pruebas de carga | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Plantillas de proyecto adicionales (versiones anteriores) | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Compatibilidad con IIS en tiempo de desarrollo | 16.0.28315.86 | Optional

## <a name="nodejs-development"></a>Desarrollo de Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Descripción:** Compile aplicaciones de red escalables con Node.js, un runtime de JavaScript controlado por eventos asincrónicos. 

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Node.Tools | Herramientas de desarrollo de Node.js | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++ Build Tools para x64/x86 (v14.20) | 16.0.28625.61 | Optional

## <a name="officesharepoint-development"></a>Desarrollo de Office y SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Descripción:** Cree complementos de Office y SharePoint, soluciones de SharePoint y complementos de VSTO mediante C#, VB y JavaScript.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 16.0.28714.129 | Obligatorio
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 16.0.28315.86 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 16.0.28517.75 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Herramientas de desarrollo de escritorio de .NET | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.MSODBC.SQL | Controlador ODBC de SQL Server | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilidades de la línea de comandos de SQL Server | 16.0.28707.177 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools para Visual Studio | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools para Office (VSTO) | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Se recomienda
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | SDK de .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.0.28315.86 | Optional
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Optional

## <a name="python-development"></a>Desarrollo de Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Descripción:** Edición, depuración, desarrollo interactivo y control de código fuente para Python.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.PythonTools | Compatibilidad con el lenguaje Python | 16.0.28625.61 | Obligatorio
Component.CPython3.x64 | Python 3 64 bits (3.7.2) | 3.7.2 | Se recomienda
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Se recomienda
Microsoft.Component.PythonTools.Minicondax64 | Miniconda de Python | 16.0.28625.61 | Se recomienda
Microsoft.Component.PythonTools.Web | Compatibilidad web con Python | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Se recomienda
Component.CPython2.x64 | Python 2 64 bits (2.7.15) | 2.7.15 | Optional
Component.CPython2.x86 | Python 2 32 bits (2.7.15) | 2.7.15 | Optional
Component.CPython3.x86 | Python 3 32 bits (3.7.2) | 3.7.2 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Administrador de bibliotecas | 16.0.28315.86 | Optional
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 16.0.28625.61 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Herramientas de desarrollo nativo de Python | 16.0.28621.142 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 16.0.28720.110 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Herramientas de compilación para Azure Cloud Services | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | Controlador ODBC de SQL Server | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilidades de la línea de comandos de SQL Server | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ Build Tools (v14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++ Build Tools para x64/x86 (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Requisitos previos de herramientas de desarrollo web y ASP.NET | 16.0.28621.142 | Optional

## <a name="universal-windows-platform-development"></a>Desarrollo de la Plataforma universal de Windows

**ID:** Microsoft.VisualStudio.Workload.Universal

**Descripción:** Cree aplicaciones para la Plataforma universal de Windows con C#, VB y, opcionalmente, C++.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.0.28315.86 | Obligatorio
Microsoft.ComponentGroup.Blend | Blend para Visual Studio | 16.0.28315.86 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.0.28517.75 | Obligatorio
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK de TypeScript 3.3 | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK de Windows 10 (10.0.17763.0) | 16.0.28517.75 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native y .NET Standard | 16.0.28516.191 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Herramientas de la Plataforma universal de Windows | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Herramientas de la Plataforma universal de Windows para Xamarin | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.0.28315.86 | Se recomienda
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Entorno de ejecución de la Plataforma universal de Windows de C++ para las herramientas de compilación de v142 | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | 16.0.28528.71 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Compatibilidad con la Plataforma universal de Windows de C++ para las herramientas de compilación de v142 (ARM64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Actualización de C++ 2019 Redistributable | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 – VS 2019 C++ Build Tools para ARM (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 – VS 2019 C++ Build Tools para ARM64 (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++ Build Tools para x64/x86 (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 – VS 2017 C++ Build Tools para ARM (v14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 – VS 2017 C++ Build Tools para ARM64 (v14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 – VS 2017 C++ Build Tools para x64/x86 (v14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | SDK de Windows 10 (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK de Windows 10 (10.0.17134.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Conectividad del dispositivo USB | 16.0.28320.51 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Herramientas de arquitectura para C++ | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Características principales de escritorio para Visual C++ | 16.0.28315.86 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Herramientas de la Plataforma universal de Windows para C++ (v142) | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Herramientas de la Plataforma universal de Windows para C++ (v141) | 16.0.28621.142 | Optional

## <a name="visual-studio-extension-development"></a>Desarrollo de extensiones de Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descripción:** Cree complementos y extensiones para Visual Studio, incluidos nuevos comandos, analizadores de código y ventanas de herramientas.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.SDK | SDK de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.Component.4.7.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7.2 | 16.0.28517.75 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo para .NET Framework 4.7.2 | 16.0.28516.191 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 16.0.28714.129 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 16.0.28625.61 | Obligatorio
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Requisitos previos para el desarrollo de extensiones de Visual Studio | 16.0.28621.142 | Obligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 16.0.28625.61 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.0.28315.86 | Se recomienda
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 16.0.28625.61 | Se recomienda
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | Optional
Microsoft.Component.CodeAnalysis.SDK | SDK de la plataforma del compilador de .NET | 16.0.28625.61 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Entorno de ejecución de la Plataforma universal de Windows de C++ para las herramientas de compilación de v142 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | 16.0.28528.71 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DslTools | SDK de modelado | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Herramientas de compilación de ATL de C++ para v142 (x86 y x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Herramientas de compilación MFC de C++ para v142 (x86 y x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++ Build Tools para x64/x86 (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | 16.0.28621.142 | Optional

## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | nombre | Versión
--- | --- | ---
Component.GitHub.VisualStudio | Extensión de GitHub para Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Generador de perfiles de Xamarin | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 16.0.28707.177
Microsoft.Component.HelpViewer | Visor de Ayuda | 16.0.28625.61
Microsoft.NetCore.1x.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para Web | 16.0.28621.142
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Integración de Office para Azure DevOps | 16.0.28625.61
Microsoft.VisualStudio.Component.Git | Git para Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Herramientas de LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Prueba de IU codificada | 16.0.28327.66
Microsoft.VisualStudio.Component.VC.ATL.ARM | Herramientas de compilación de ATL de C++ para v142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Herramientas de compilación de ATL de C++ para v142 con mitigaciones de Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Herramientas de compilación de ATL de C++ para v142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Herramientas de compilación de ATL de C++ para v142 con mitigaciones de Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Herramientas de compilación de ATL de C++ para v142 con mitigaciones de Spectre (x86 y x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Herramientas de compilación MFC de C++ para v142 con mitigaciones de Spectre (x86 y x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM | Herramientas de compilación MFC de C++ para v142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Herramientas de compilación MFC de C++ para v142 con mitigaciones de Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Herramientas de compilación MFC de C++ para v142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Herramientas de compilación MFC de C++ para v142 con mitigaciones de Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Redist.MSM | MSM de C++ 2019 Redistributable | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 – Bibliotecas con mitigaciones de Spectre de VS 2019 C++ para ARM (v14.20) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 – Bibliotecas con mitigaciones de Spectre de VS 2019 C++ para ARM64 (v14.20) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 – Bibliotecas con mitigaciones de Spectre de VS 2019 C++ para x64/x86 (v14.20)  | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 – Bibliotecas con mitigaciones de Spectre de VS 2017 C++ para ARM (v14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 – Bibliotecas con mitigaciones de Spectre de VS 2017 C++ para ARM64 (v14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL | Herramientas de compilación de ATL de C++ para v141 (x86 y x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | Herramientas de compilación de ATL de C++ para v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | Herramientas de compilación de ATL de C++ para v141 con mitigaciones de Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | Herramientas de compilación de ATL de C++ para v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | Herramientas de compilación de ATL de C++ para v141 con mitigaciones de Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | Herramientas de compilación de ATL de C++ para v141 con mitigaciones de Spectre (x86 y x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | Compatibilidad con C++/CLI para las herramientas de compilación de v141 | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC | Herramientas de compilación MFC de C++ para v141 (x86 y x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | Herramientas de compilación MFC de C++ para v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | Herramientas de compilación MFC de C++ para v141 con mitigaciones de Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | Herramientas de compilación MFC de C++ para v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | Herramientas de compilación MFC de C++ para v141 con mitigaciones de Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | Herramientas de compilación MFC de C++ para v141 con mitigaciones de Spectre (x86 y x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 – Bibliotecas con mitigaciones de Spectre de VS 2017 C++ para x64/x86 (v14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Herramientas de compatibilidad de Windows XP con C++ para VS 2017 (v141) [en desuso] | 16.0.28625.61
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.0.28621.142
