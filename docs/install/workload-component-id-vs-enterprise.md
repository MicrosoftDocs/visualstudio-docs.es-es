---
title: Identificadores de componente y carga de trabajo de Visual Studio Enterprise 2017 | Microsoft Docs
description: "Uso de identificadores de componente y carga de trabajo para instalar Visual Studio mediante la línea de comandos o especificarlo como una dependencia en un manifiesto VSIX"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 10/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-acquisition
ms.assetid: be73e3af-d87b-4d14-bd08-2e4bda074fb3
ms.openlocfilehash: a218e0e9fe684f348d8f6e031895031172a76163
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2017
---
# <a name="visual-studio-enterprise-2017-component-directory"></a>Directorio de componentes de Visual Studio Enterprise 2017

Las tablas de esta página presentan los identificadores que puede usar para instalar Visual Studio mediante la línea de comandos o que puede especificar como una dependencia en un manifiesto VSIX. Tenga en cuenta que agregaremos componentes adicionales a medida que se publiquen actualizaciones de Visual Studio.

Tenga en cuenta también lo siguiente sobre la página:

* Cada carga de trabajo tiene su propia sección, seguida por el identificador de la carga de trabajo y una tabla de los componentes que están disponibles para la carga de trabajo.
* De forma predeterminada, los componentes con carácter **Obligatorio** se instalarán cuando se instala la carga de trabajo.
* Si lo desea, también puede instalar los componentes con la marca **Recomendado** y **Opcional**.
* También hemos agregado una sección que muestra los componentes adicionales que no están asociados a ninguna carga de trabajo.

Al establecer las dependencias del manifiesto de VSIX, debe especificar solo identificadores de componentes. Utilice las tablas de esta página para determinar las dependencias de componente mínimas. En algunos casos, esto podría significar que se especifique solo un componente de una carga de trabajo. En otros escenarios, puede significar que especifique varios componentes de una sola carga de trabajo o varios componentes de varias cargas de trabajo. Para obtener más información, consulte la página [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Migración de proyectos de extensibilidad a Visual Studio 2017).

Para obtener más información acerca de cómo utilizar estos identificadores, vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Y, para obtener una lista de los identificadores de componente y carga de trabajo para otros productos, consulte la página [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (Identificadores de componente y carga de trabajo de Visual Studio 2017).

## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2017"></a>Editor de núcleo de Visual Studio (incluido con Visual Studio Enterprise 2017)

**Id.:** Microsoft.VisualStudio.Workload.CoreEditor

**Descripción:** la experiencia del shell principal de Visual Studio, que incluye edición de código compatible con la sintaxis, control de código fuente y administración de elementos de trabajo.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor de núcleo de Visual Studio | 15.0.26606.0 | Obligatorio


## <a name="azure-development"></a>Desarrollo de Azure

**Id.:** Microsoft.VisualStudio.Workload.Azure

**Descripción:** Azure SDK, herramientas y proyectos de desarrollo de aplicaciones en la nube y creación de recursos.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Obligatorio
Component.Microsoft.VisualStudio.Web.AzureFunctions | Herramientas de WebJobs de Microsoft Azure | 15.0.26720.2 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatorio
Microsoft.Component.NetFX.Core.Runtime | Tiempo de ejecución de .NET Core | 15.0.26208.0 | Obligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Obligatorio
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.0.26606.0 | Obligatorio
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 2.0 | 15.0.26919.1 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 2.0 | 15.0.26919.1 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.0.26823.1 | Obligatorio
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 1.10.50614.2 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.0.26419.1 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Requisitos previos del desarrollo de Azure | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de WebJobs de Microsoft Azure | 15.0.26720.2 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Obligatorio
Microsoft.Component.Azure.DataLake.Tools | Herramientas de Azure Data Lake y Stream Analytics | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | SDK de Azure Mobile Apps | 15.0.26504.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Herramientas principales de Azure Resource Manager | 15.0.26906.1 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Herramientas de Service Fabric | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Herramientas de Azure Cloud Services | 15.0.26504.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Herramientas de Azure Resource Manager | 15.0.26919.1 | Se recomienda
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 15.0.26419.1 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 15.0.26606.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para escritorio | 15.0.26919.1 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para Web | 15.0.26919.1 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.PowerShell.Tools | Herramientas de PowerShell | 3.0.552 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26606.0 | Optional


## <a name="data-storage-and-processing"></a>Almacenamiento y procesamiento de datos

**Id.:** Microsoft.VisualStudio.Workload.Data

**Descripción:** conecte, desarrolle y pruebe soluciones de datos con SQL Server, Azure Data Lake, Hadoop o Azure ML.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Se recomienda
Component.Redgate.ReadyRoll | Redgate ReadyRoll Core | 1.14.2.3918 | Se recomienda
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt Core | 8.0.2.1513 | Se recomienda
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 2.4.2.1439 | Se recomienda
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Se recomienda
Microsoft.Component.Azure.DataLake.Tools | Herramientas de Azure Data Lake y Stream Analytics | 15.0.26823.1 | Se recomienda
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Se recomienda
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Se recomienda
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 1.10.50614.2 | Se recomienda
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.0.26419.1 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.0.26606.0 | Optional


## <a name="data-science-and-analytical-applications"></a>Aplicaciones analíticas y de ciencia de datos

**Id.:** Microsoft.VisualStudio.Workload.DataScience

**Descripción**: lenguajes y herramientas para crear aplicaciones de ciencia de datos, como Python, R y F#.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Anaconda3.x64 | Anaconda3 64 bits (4.4.0) | 4.4.0 | Se recomienda
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Se recomienda
Microsoft.Component.CookiecutterTools | Compatibilidad con plantillas de Cookiecutter | 15.0.26621.2 | Se recomienda
Microsoft.Component.PythonTools | Compatibilidad con el lenguaje Python | 15.0.26823.1 | Se recomienda
Microsoft.Component.PythonTools.Web | Compatibilidad web con Python | 15.0.26606.0 | Se recomienda
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.0.26208.0 | Se recomienda
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 1.10.50614.2 | Se recomienda
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.R.Open | Cliente de Microsoft R (3.3.2) | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.RHost | Compatibilidad del entorno de tiempo de ejecución con herramientas de desarrollo de R | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.RTools | Compatibilidad con el lenguaje R | 15.0.26919.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Component.Anaconda2.x64 | Anaconda2 64 bits (4.4.0) | 4.4.0 | Optional
Component.Anaconda2.x86 | Anaconda2 32 bits (4.4.0) | 4.4.0 | Optional
Component.Anaconda3.x86 | Anaconda3 32 bits (4.4.0) | 4.4.0 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Herramientas de desarrollo nativo de Python | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de herramientas de VC++ 2015.3 v140 para el escritorio (x86, x64) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK de Windows 10 (10.0.16299.0) para escritorio C++ [x86 and x64] | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.0.27004.2002 | Optional


## <a name="net-desktop-development"></a>Desarrollo de escritorio de .NET

**Id.:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descripción:**: compile aplicaciones de WPF, Windows Forms y consola mediante C#, Visual Basic y F#.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 15.0.26823.1 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.0.26419.1 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Herramientas de desarrollo de escritorio de .NET | 15.0.26906.1 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Obligatorio
Microsoft.ComponentGroup.Blend | Blend para Visual Studio | 15.0.26711.1 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.EntityFramework | Herramientas de Entity Framework 6 | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Se recomienda
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 15.0.26419.1 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 15.0.26606.0 | Optional
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.0.26606.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para escritorio | 15.0.26919.1 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 2.0 | 15.0.26919.1 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | 15.0.26208.0 | Optional


## <a name="game-development-with-unity"></a>Desarrollo de juegos con Unity

**Id.:** Microsoft.VisualStudio.Workload.ManagedGame

**Descripción:** cree juegos en 2D y 3D con Unity, un entorno de desarrollo multiplataforma muy eficaz.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Herramientas de desarrollo para .NET Framework 3.5 | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools para Unity | 15.0.26823.1 | Obligatorio
Component.UnityEngine.x64 | Editor Unity 2017.1 de 64 bits | 15.0.26919.1 | Se recomienda
Component.UnityEngine.x86 | Editor Unity 5.6 de 32 bits | 15.0.26919.1 | Se recomienda


## <a name="linux-development-with-c"></a>Desarrollo para Linux con C++

**Id.:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descripción:** cree y depure aplicaciones que se ejecutan en un entorno de Linux.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.MDD.Linux | Visual C++ para desarrollo de aplicaciones para Linux | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.0.26621.2 | Obligatorio
Component.Linux.CMake | Herramientas de Visual C++ para CMake y Linux | 15.0.27004.2002 | Se recomienda
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK de Windows 10 (10.0.16299.0) para escritorio C++ [x86 and x64] | 15.0.27004.2002 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27004.2002 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.0.27004.2002 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda


## <a name="desktop-development-with-c"></a>Desarrollo para el escritorio con C++

**Id.:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descripción:** compile aplicaciones clásicas basadas en Windows con la tecnología del conjunto de herramientas de Visual C++, ATL y características opcionales como MFC y C++/CLI.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 15.0.26823.1 | Obligatorio
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26906.1 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Actualización de Visual C++ 2017 Redistributable | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Herramientas de arquitectura para C++ | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Características principales de escritorio para Visual C++ | 15.0.26621.2 | Obligatorio
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Se recomienda
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.CMake.Project | Herramientas de Visual C++ para CMake | 15.0.27004.2002 | Se recomienda
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK de Windows 10 (10.0.16299.0) para escritorio C++ [x86 and x64] | 15.0.27004.2002 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27004.2002 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.0.27004.2002 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Component.Incredibuild | IncrediBuild: Aceleración de compilación | 15.0.26919.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.1 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de herramientas de VC++ 2015.3 v140 para el escritorio (x86, x64) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Compatibilidad con ATL para Visual C++ | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Compatibilidad con MFC y ATL (x86 y x64) | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimental) | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Compatibilidad con C++/CLI | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos para biblioteca estándar (experimental) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK de Windows 10 (10.0.15063.0) para escritorio C++ [x86 y x64] | 15.0.26929.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK de Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK de Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.WinXP | Soporte de Windows XP para C++ | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK de Windows 8.1 y SDK de UCRT | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Soporte de Windows XP para C++ | 15.0.26208.0 | Optional


## <a name="game-development-with-c"></a>Desarrollo de juegos con C++

**Id.:** Microsoft.VisualStudio.Workload.NativeGame

**Descripción:** use toda la capacidad de C++ para crear juegos profesionales con tecnología de DirectX, Unreal o Cocos2d.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Actualización de Visual C++ 2017 Redistributable | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK de Windows 10 (10.0.16299.0) para escritorio C++ [x86 and x64] | 15.0.27004.2002 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27004.2002 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.0.27004.2002 | Se recomienda
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.9 | Optional
Component.Android.SDK23.Private | Instalación de Android SDK (nivel de API 23) (instalación local) | 15.0.26906.1 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | Optional
Component.Cocos | Cocos | 15.0.26906.1 | Optional
Component.Incredibuild | IncrediBuild: Aceleración de compilación | 15.0.26919.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.1 | Optional
Component.JavaJDK | Kit de desarrollo de Java SE (8.0.1120.15) | 15.0.26403.0 | Optional
Component.MDD.Android | Herramientas de desarrollo de Android en C ++ | 15.0.26606.0 | Optional
Component.Unreal | Instalador de Unreal Engine | 15.0.26621.2 | Optional
Component.Unreal.Android | Compatibilidad de Visual Studio con Android para Unreal Engine | 15.0.26919.1 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK de Windows 10 (10.0.15063.0) para escritorio C++ [x86 y x64] | 15.0.26929.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK de Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK de Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK de Windows 8.1 y SDK de UCRT | 15.0.26208.0 | Optional


## <a name="mobile-development-with-c"></a>Desarrollo móvil con C++

**Id.:** Microsoft.VisualStudio.Workload.NativeMobile

**Descripción:** cree aplicaciones multiplataforma para iOS, Android o Windows con C++.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.0.26606.0 | Obligatorio
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.6 | Se recomienda
Component.Android.SDK19 | Instalación de Android SDK (niveles de API 19 y 21) | 15.0.26621.2 | Se recomienda
Component.Android.SDK22 | Instalación de Android SDK (nivel de API 22) | 15.0.26208.0 | Se recomienda
Component.Android.SDK25 | Instalación de Android SDK (nivel de API 25) | 15.0.26919.1 | Se recomienda
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | Se recomienda
Component.MDD.Android | Herramientas de desarrollo de Android en C ++ | 15.0.26606.0 | Se recomienda
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.9 | Optional
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 bits) | 12.1.10 | Optional
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 bits) | 13.1.7 | Optional
Component.Android.SDK23 | Instalación de Android SDK (nivel de API 23) (instalación global) | 15.0.26906.1 | Optional
Component.Google.Android.Emulator.API23.V2 | Google Android Emulator (nivel de API 23) (instalación global) | 15.0.26906.1 | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (instalación global) | 15.0.26919.1 | Optional
Component.Incredibuild | IncrediBuild: Aceleración de compilación | 15.0.26919.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.1 | Optional
Component.JavaJDK | Kit de desarrollo de Java SE (8.0.1120.15) | 15.0.26403.0 | Optional
Component.MDD.IOS | Herramientas de desarrollo de iOS en C++ | 15.0.26621.2 | Optional


## <a name="net-core-cross-platform-development"></a>Desarrollo multiplataforma de .NET Core

**Id.:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descripción:** Compile aplicaciones multiplataforma mediante NET Core, ASP.NET Core, HTML, JavaScript y herramientas de desarrollo de contenedor.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 2.0 | 15.0.26919.1 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 2.0 | 15.0.26919.1 | Obligatorio
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Se recomienda
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Se recomienda
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Se recomienda
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Se recomienda
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 1.10.50614.2 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 15.0.26724.1 | Se recomienda
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Se recomienda
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.0.26419.1 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para escritorio | 15.0.26919.1 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para Web | 15.0.26919.1 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Compatibilidad con IIS en tiempo de desarrollo | 15.0.26720.2 | Optional


## <a name="mobile-development-with-net"></a>Desarrollo móvil con .NET

**Id.:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descripción:** cree aplicaciones multiplataforma para iOS, Android o Windows con Xamarin.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Android.SDK25 | Instalación de Android SDK (nivel de API 25) | 15.0.26919.1 | Obligatorio
Component.Google.Android.Emulator.API25 | Google Android Emulator (nivel de API 25) | 15.0.26929.2 | Obligatorio
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (instalación global) | 15.0.26919.1 | Obligatorio
Component.JavaJDK | Kit de desarrollo de Java SE (8.0.1120.15) | 15.0.26403.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Obligatorio
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.6 | Se recomienda
Component.Xamarin | Xamarin | 15.0.26711.1 | Se recomienda
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26606.0 | Se recomienda
Component.Xamarin.Profiler | Generador de perfiles de Xamarin | 15.0.26823.1 | Se recomienda
Component.Xamarin.RemotedSimulator | Simulador remoto de Xamarin | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.Merq | Herramientas internas comunes de Xamarin | 15.0.26720.2 | Se recomienda
Microsoft.VisualStudio.Component.MonoDebugger | Depurador de Mono | 15.0.26720.2 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Optional
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulador de Windows 10 Mobile (Creators Update) | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Herramientas de la Plataforma universal de Windows para Xamarin | 15.0.27004.2002 | Optional


## <a name="aspnet-and-web-development"></a>Desarrollo web y ASP.NET

**Id.:** Microsoft.VisualStudio.Workload.NetWeb

**Descripción:** compile aplicaciones web mediante ASP.NET, ASP.NET Core, HTML, JavaScript y herramientas de desarrollo de contenedores.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.0.26606.0 | Obligatorio
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Herramientas de desarrollo de .NET Core 2.0 | 15.0.26919.1 | Obligatorio
Microsoft.NetCore.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 2.0 | 15.0.26919.1 | Obligatorio
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Se recomienda
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Se recomienda
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Se recomienda
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Se recomienda
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.0.26823.1 | Se recomienda
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 1.10.50614.2 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.DockerTools | Herramientas de desarrollo de contenedor | 15.0.26724.1 | Se recomienda
Microsoft.VisualStudio.Component.EntityFramework | Herramientas de Entity Framework 6 | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26720.2 | Se recomienda
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.0.26419.1 | Se recomienda
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Microsoft.Net.Component.4.6.2.SDK | SDK de .NET Framework 4.6.2 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.2 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | SDK de .NET Framework 4.7 | 15.0.26419.1 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Paquete de compatibilidad de .NET Framework 4.7 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Herramientas de desarrollo de .NET Framework 4.6.2 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Herramientas de desarrollo para .NET Framework 4.7 | 15.0.26606.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para escritorio | 15.0.26919.1 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | Herramientas de desarrollo de .NET Core 1.0 - 1.1 para Web | 15.0.26919.1 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.FSharp | Compatibilidad con el idioma F# | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Herramientas de rendimiento web y pruebas de carga | 15.0.26606.0 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Compatibilidad con IIS en tiempo de desarrollo | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.0.26606.0 | Optional


## <a name="nodejs-development"></a>Desarrollo de Node.js

**Id.:** Microsoft.VisualStudio.Workload.Node

**Descripción:** cree aplicaciones de red escalables con Node.js, un tiempo de ejecución de JavaScript asincrónico y orientado a eventos.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Node.Tools | Compatibilidad con Node.js | 15.0.26823.1 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 1.10.50614.2 | Se recomienda
Microsoft.VisualStudio.Component.Git | Git para Windows | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | 15.0.26823.1 | Optional


## <a name="officesharepoint-development"></a>Desarrollo de Office y SharePoint

**Id.:** Microsoft.VisualStudio.Workload.Office

**Descripción:** cree complementos de Office y SharePoint, soluciones de SharePoint y complementos VSTO mediante C#, VB y JavaScript.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 1.10.50614.2 | Obligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 15.0.26823.1 | Obligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.0.26419.1 | Obligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Herramientas de desarrollo de escritorio de .NET | 15.0.26906.1 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools para Visual Studio | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools para Office (VSTO) | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Optional


## <a name="python-development"></a>Desarrollo de Python

**Id.:** Microsoft.VisualStudio.Workload.Python

**Descripción:** edición, depuración, desarrollo interactivo y control de código fuente para Python.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.CPython3.x64 | Python 3 64 bits (3.6.2) | 3.6.2 | Se recomienda
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Se recomienda
Microsoft.Component.CookiecutterTools | Compatibilidad con plantillas de Cookiecutter | 15.0.26621.2 | Se recomienda
Microsoft.Component.PythonTools | Compatibilidad con el lenguaje Python | 15.0.26823.1 | Se recomienda
Microsoft.Component.PythonTools.Web | Compatibilidad web con Python | 15.0.26606.0 | Se recomienda
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 1.10.50614.2 | Se recomienda
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Se recomienda
Component.Anaconda2.x64 | Anaconda2 64 bits (4.4.0) | 4.4.0 | Optional
Component.Anaconda2.x86 | Anaconda2 32 bits (4.4.0) | 4.4.0 | Optional
Component.Anaconda3.x64 | Anaconda3 64 bits (4.4.0) | 4.4.0 | Optional
Component.Anaconda3.x86 | Anaconda3 32 bits (4.4.0) | 4.4.0 | Optional
Component.CPython2.x64 | Python 2 de 64 bits (2.7.13) | 2.7.13 | Opcional
Component.CPython2.x86 | Python 2 de 32 bits (2.7.13) | 2.7.13 | Opcional
Component.CPython3.x86 | Python 3 32 bits (3.6.2) | 3.6.2 | Optional
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Optional
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Optional
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Optional
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Opcional
Microsoft.Component.PythonTools.UWP | Compatibilidad con IoT de Python | 15.0.26606.0 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Herramientas de desarrollo nativo de Python | 15.0.27004.2002 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Azure Compute | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Azure Storage | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Herramientas principales de Azure Cloud Services | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo de carga de trabajo de escritorio administrado | 15.0.26419.1 | Opcional
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de herramientas de VC++ 2015.3 v140 para el escritorio (x86, x64) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Herramientas de generación de perfiles de C++ | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.Web | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK de Windows 10 (10.0.16299.0) para escritorio C++ [x86 and x64] | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Herramientas de desarrollo web y ASP.NET | 15.0.26606.0 | Optional


## <a name="universal-windows-platform-development"></a>Desarrollo de la Plataforma universal de Windows

**Id.:** Microsoft.VisualStudio.Workload.Universal

**Descripción:** cree aplicaciones para la Plataforma universal de Windows con C#, VB, JavaScript u opcionalmente C++.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Obligatorio
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Obligatorio
Microsoft.ComponentGroup.Blend | Blend para Visual Studio | 15.0.26711.1 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.UWP.Support | Herramientas de la Plataforma universal de Windows | 15.0.26906.1 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27004.2002 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Herramientas de la Plataforma universal de Windows para Cordova | 15.0.27004.2002 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Herramientas de la Plataforma universal de Windows para Xamarin | 15.0.27004.2002 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK de Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK de Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.26621.2 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.Win10SDK_10.0.15063.UWP.All | SDK de Windows 10 (10.0.15063.0) para UWP | 15.0.27004.2002 | Se recomienda
Microsoft.Component.VC.Runtime.OSSupport | Tiempo de ejecución de Visual C++ para UWP | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos y creador de perfiles GPU para DirectX | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | SDK de Windows 8.1 de herramientas gráficas | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulador de Windows 10 Mobile (Creators Update) | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Bibliotecas y compiladores de Visual Studio C++ para ARM | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK de Windows 10 (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK de Windows 10 (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Herramientas de la Plataforma universal de Windows de C++ | 15.0.27004.2002 | Optional


## <a name="visual-studio-extension-development"></a>Desarrollo de extensiones de Visual Studio

**Id.:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descripción:** cree complementos y extensiones para Visual Studio, como nuevos comandos, analizadores de código y ventanas de herramientas.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Paquete de compatibilidad de biblioteca portátil de .NET | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Requisitos previos para el desarrollo de extensiones de Visual Studio | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.CodeClone | Clon de código | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.CodeMap | Mapa de código | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Validación de dependencias en vivo | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Se recomienda
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 15.0.26906.1 | Se recomienda
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 15.0.26606.0 | Se recomienda
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Se recomienda
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Herramientas de arquitectura y análisis | 15.0.26208.0 | Se recomienda
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Tiempo de ejecución de Visual C++ para UWP | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Diseñador de clases | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DslTools | SDK de modelado | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Compatibilidad con ATL para Visual C++ | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Compatibilidad con MFC y ATL (x86 y x64) | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Características principales de Visual Studio C++ | 15.0.26606.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de herramientas de VC++ 2017 v141 (x86,x64) | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.0.26919.1 | Optional


## <a name="mobile-development-with-javascript"></a>Desarrollo móvil con JavaScript

**Id.:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Descripción:** compile aplicaciones de Android, iOS y UWP con Herramientas para Apache Cordova.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | Nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Conjunto de herramientas de Cordova 6.3.1 | 15.0.26504.0 | Obligatorio
Component.Microsoft.VisualStudio.RazorExtension | Servicios de lenguaje Razor | 15.0.26720.2 | Obligatorio
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Cordova | Características principales del desarrollo móvil con JavaScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnósticos de JavaScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript Project System y herramientas compartidas | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Compatibilidad con lenguaje JavaScript y TypeScript | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.26711.1 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desarrollo web y ASP.NET | 15.0.26606.0 | Obligatorio
Component.Android.SDK23.Private | Instalación de Android SDK (nivel de API 23) (instalación local) | 15.0.26906.1 | Optional
Component.Google.Android.Emulator.API23.Private | Google Android Emulator (nivel de API 23) (instalación local) | 15.0.26906.1 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (instalación local) | 15.0.26919.1 | Optional
Component.JavaJDK | Kit de desarrollo de Java SE (8.0.1120.15) | 15.0.26403.0 | Optional
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.26919.1 | Optional
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Herramientas para generación de perfiles de .NET | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.Git | Git para Windows | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics | Editores de imágenes y modelos 3D | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulador de Windows 10 Mobile (Creators Update) | 15.0.26711.1 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Herramientas de la Plataforma universal de Windows para Cordova | 15.0.27004.2002 | Optional


## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | Nombre | Versión
--- | --- | ---
Component.Android.Emulator | Emulador de Visual Studio para Android | 15.0.26711.1
Component.Android.NDK.R11C | Android NDK (R11C) | 11.3.13
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 bits) | 11.3.15
Component.GitHub.VisualStudio | Extensión de GitHub para Visual Studio | 2.2.0.10
Microsoft.Component.Blend.SDK.WPF | SDK de Blend para Visual Studio para .NET | 15.0.26929.2
Microsoft.Component.HelpViewer | Visor de Ayuda | 15.0.26711.1
Microsoft.VisualStudio.Component.LinqToSql | Herramientas de LINQ to SQL | 15.0.26208.0
Microsoft.VisualStudio.Component.Phone.Emulator | Emulador de Windows 10 Mobile (Anniversary Edition) | 15.0.26711.1
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Prueba de IU codificada | 15.0.26606.0
Microsoft.VisualStudio.Component.TestTools.Core | Características principales de las herramientas de pruebas | 15.0.26606.0
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.0.26711.1
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.0.26606.0
Microsoft.VisualStudio.Component.TypeScript.2.0 | SDK de TypeScript 2.0 | 15.0.26504.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | 15.0.26208.0
Microsoft.VisualStudio.Component.TypeScript.2.2 | SDK de TypeScript 2.2 | 15.0.26504.0
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Bibliotecas y compiladores de Visual C++ para ARM64 | 15.0.26906.1
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | SDK de Windows 10 SDK (10.0.16299.0) para escritorio C++ [ARM y ARM64] | 15.0.27004.2002

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)
