---
title: Identificadores de componentes y cargas de trabajo de Visual Studio Build Tools 2017
description: Uso de identificadores de componente y carga de trabajo de Visual Studio para crear aplicaciones clásicas basadas en Windows
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload:
- multiple
ms.openlocfilehash: 958e4e842468e871cd9aa65f0a20b87a84aeb4ca
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607866"
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Directorio de componentes de Visual Studio Build Tools 2017

Las tablas de esta página presentan los identificadores que puede usar para instalar Visual Studio mediante la línea de comandos o que puede especificar como una dependencia en un manifiesto VSIX. Tenga en cuenta que agregaremos componentes adicionales a medida que se publiquen actualizaciones de Visual Studio.

Tenga en cuenta también lo siguiente sobre la página:

* Cada carga de trabajo tiene su propia sección, seguida por el identificador de la carga de trabajo y una tabla de los componentes que están disponibles para la carga de trabajo.
* De forma predeterminada, los componentes con carácter **Obligatorio** se instalarán cuando se instala la carga de trabajo.
* Si lo desea, también puede instalar los componentes con la marca **Recomendado** y **Opcional**.
* También hemos agregado una sección que muestra los componentes adicionales que no están asociados a ninguna carga de trabajo.

Al establecer las dependencias del manifiesto de VSIX, debe especificar solo identificadores de componentes. Utilice las tablas de esta página para determinar las dependencias de componente mínimas. En algunos casos, esto podría significar que se especifique solo un componente de una carga de trabajo. En otros escenarios, puede significar que especifique varios componentes de una sola carga de trabajo o varios componentes de varias cargas de trabajo. Para obtener más información, consulte la página [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Migración de proyectos de extensibilidad a Visual Studio 2017).

Para obtener más información acerca de cómo utilizar estos identificadores, vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Y, para obtener una lista de los identificadores de componente y carga de trabajo para otros productos, consulte la página [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (Identificadores de componente y carga de trabajo de Visual Studio 2017).

## <a name="azure-development-build-tools"></a>Herramientas de compilación de desarrollo para Azure

**Id.:** Microsoft.VisualStudio.Workload.AzureBuildTools

**Descripción:** tareas y objetivos de MSBuild para la creación de aplicaciones de Azure.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Herramientas de creación de Azure | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas de Azure para .NET | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Herramientas de compilación para Azure Cloud Services | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Herramientas de desarrollo de contenedor: herramientas de compilación | 15.7.27617.1 | Obligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Herramientas de compilación de desarrollo de WCF | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Herramientas de compilación de desarrollo web | 15.8.27729.1 | Obligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Se recomienda
Microsoft.VisualStudio.Component.AspNet45 | Características avanzadas de ASP.NET | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Se recomienda
Microsoft.Net.Component.3.5.DeveloperTools | Herramientas de desarrollo para .NET Framework 3.5 | 15.6.27406.0 | Optional
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

## <a name="data-storage-and-processing-build-tools"></a>Herramientas de procesamiento de compilación y almacenamiento de datos

**Id.:** Microsoft.VisualStudio.Workload.DataBuildTools

**Descripción:** Crear proyectos de base de datos de SQL Server

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Se recomienda
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Component.SQL.SSDTBuildSku | SQL Server Data Tools: herramientas de compilación | 15.8.27825.0 | Se recomienda
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Se recomienda

## <a name="net-desktop-build-tools"></a>Herramientas de compilación para escritorio de .NET

**Id.:** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**Descripción:** Herramientas para compilar aplicaciones de consola, WPF y Windows Forms con C#, Visual Basic y F#.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.Component.ClickOnce.MSBuild | Herramientas de compilación de ClickOnce | 15.7.27617.1 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 2.0 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Se recomienda
Microsoft.VisualStudio.Component.TestTools.BuildTools | Características principales de las herramientas de pruebas - herramientas de compilación | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Herramientas de compilación de desarrollo de WCF | 15.6.27309.0 | Se recomienda
Microsoft.Net.Component.3.5.DeveloperTools | Herramientas de desarrollo para .NET Framework 3.5 | 15.6.27406.0 | Optional
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
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.FSharp.MSBuild | compilador de F# | 15.8.27825.0 | Optional

## <a name="msbuild-tools"></a>Herramientas de MSBuild

**Id.:** Microsoft.VisualStudio.Workload.MSBuildTools

**Descripción:** proporciona las herramientas necesarias para crear aplicaciones basadas en MSBuild.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools Core | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio

## <a name="net-core-build-tools"></a>Herramientas de compilación de .NET Core

**Id.:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Descripción:** Herramientas para crear aplicaciones con .NET Core, ASP.NET Core, HTML/JavaScript y Containers.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Obligatorio
Microsoft.NetCore.BuildTools.ComponentGroup | Herramientas de compilación de .NET Core | 15.8.27906.1 | Obligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.Net.Core.Component.SDK | Herramientas de desarrollo de .NET Core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Herramientas de desarrollo de .NET Core 1.0 - 1.1 | 15.6.27406.0 | Optional

## <a name="nodejs-build-tools"></a>Herramientas de compilación de Node.js

**ID:** Microsoft.VisualStudio.Workload.NodeBuildTools

**Descripción:** Tareas de MSBuild y destinos para compilar aplicaciones de red escalables utilizando Node.js, un tiempo de ejecución de JavaScript impulsado por un evento asincrónico.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Soporte de MSBuild para Node.js | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio

## <a name="officesharepoint-build-tools"></a>Herramientas de compilación para Office o SharePoint

**Id.:** Microsoft.VisualStudio.Workload.OfficeBuildTools

**Descripción:** Crear complementos de Office y SharePoint, y de VSTO.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | Herramientas de compilación de ClickOnce | 15.7.27617.1 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Herramientas de compilación de desarrollo para Office o SharePoint | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.Workflow.BuildTools | Herramientas de compilación de Windows Workflow Foundation | 15.8.27906.1 | Obligatorio
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Herramientas de compilación de desarrollo de WCF | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Herramientas de compilación de desarrollo web | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | Herramientas de compilación de Visual Studio Tools para Office (VSTO) | 15.7.27617.1 | Se recomienda
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

## <a name="universal-windows-platform-build-tools"></a>Herramientas de compilación de la Plataforma universal de Windows

**Id.:** Microsoft.VisualStudio.Workload.UniversalBuildTools

**Descripción:** Proporciona las herramientas necesarias para compilar aplicaciones de la Plataforma universal de Windows.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Obligatorio
Microsoft.Component.VC.Runtime.OSSupport | Tiempo de ejecución de Visual C++ para UWP | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.7.1.SDK | SDK de .NET Framework 4.7.1 | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.Tools.ARM | Bibliotecas y compiladores de Visual Studio C++ para ARM | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | Requisitos previos de compilación de la Plataforma universal de Windows | 15.8.27705.0 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK de Windows 10 (10.0.17134.0) | 15.8.27924.0 | Se recomienda
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
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | SDK de Windows 10 (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | SDK de Windows 10 (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="visual-c-build-tools"></a>Herramientas de compilación de Visual C++

**Id.:** Microsoft.VisualStudio.Workload.VCTools

**Descripción:** Compila aplicaciones de escritorio de Windows con el conjunto de herramientas de Microsoft C++, ATL o MFC.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Características principales de Visual C++ Build Tools | 15.8.27729.1 | Obligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Actualización de Visual C++ 2017 Redistributable | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Entorno de tiempo de ejecución de C de Windows Universal | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.TestTools.BuildTools | Características principales de las herramientas de pruebas - herramientas de compilación | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Component.VC.CMake.Project | Herramientas de Visual C++ para CMake | 15.8.27906.1 | Se recomienda
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK de Windows 10 (10.0.17134.0) | 15.8.27924.0 | Se recomienda
Microsoft.Component.VC.Runtime.UCRTSDK | SDK de Windows Universal CRT | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de herramientas de VC++ 2015.3 v14.00 (v140) para escritorio | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.ATL | ATL de Visual C++ para x86 y x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC de Visual C++ para x86 y x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Compatibilidad con C++/CLI | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos para biblioteca estándar (experimental) | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Bibliotecas y compiladores de Visual Studio C++ para ARM | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Bibliotecas y compiladores de Visual C++ para ARM64 | 15.9.28230.55 | Optional
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
Microsoft.VisualStudio.Component.Windows81SDK | SDK de Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.WinXP | Soporte de Windows XP para C++ | 15.8.27924.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK de Windows 8.1 y SDK de UCRT | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Soporte de Windows XP para C++ | 15.8.27705.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | SDK de Windows 10 (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | SDK de Windows 10 (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="visual-studio-extension-development"></a>Desarrollo de extensiones de Visual Studio

**Id.:** Microsoft.VisualStudio.Workload.VisualStudioExtensionBuildTools

**Descripción:** Herramientas para compilar complementos y extensiones para Visual Studio, incluidos nuevos comandos, analizadores de código y ventanas de herramientas.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Microsoft.VisualStudio.Component.VSSDKBuildTools | SDK de Visual Studio Build Tools Core | 15.8.27924.0 | Obligatorio
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtensionBuildTools.Prerequisites | Requisitos previos para el desarrollo de extensiones de Visual Studio | 15.8.27729.1 | Obligatorio
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Tiempo de ejecución de Visual C++ para UWP | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATL | ATL de Visual C++ para x86 y x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC de Visual C++ para x86 y x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Últimas herramientas v141 de VC++ 2017 versión 15.9 v14.16 | 15.9.28230.55 | Optional

## <a name="web-development-build-tools"></a>Herramientas de compilación de desarrollo web

**Id.:** Microsoft.VisualStudio.Workload.WebBuildTools

**Descripción:** tareas y objetivos de MSBuild para la creación de aplicaciones web.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.8.27825.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.TypeScript.3.1 | SDK de TypeScript 3.1 | 15.0.28218.60 | Obligatorio
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Herramientas de compilación de desarrollo web | 15.8.27729.1 | Obligatorio
Microsoft.Component.ClickOnce.MSBuild | Herramientas de compilación de ClickOnce | 15.7.27617.1 | Se recomienda
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.6.27406.0 | Se recomienda
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.6.27406.0 | Se recomienda
Microsoft.Net.Core.Component.SDK.2.1 | Herramientas de desarrollo de .NET Core 2.1 | 15.8.27924.0 | Se recomienda
Microsoft.VisualStudio.Component.AspNet45 | Características avanzadas de ASP.NET | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Herramientas de desarrollo de contenedor: herramientas de compilación | 15.7.27617.1 | Se recomienda
Microsoft.VisualStudio.Component.TestTools.BuildTools | Características principales de las herramientas de pruebas - herramientas de compilación | 15.7.27625.0 | Se recomienda
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Se recomienda
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Herramientas de compilación de desarrollo de WCF | 15.6.27309.0 | Se recomienda
Microsoft.Net.Component.3.5.DeveloperTools | Herramientas de desarrollo para .NET Framework 3.5 | 15.6.27406.0 | Optional
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

## <a name="mobile-development-with-net"></a>Desarrollo móvil con .NET

**Id.:** Microsoft.VisualStudio.Workload.XamarinBuildTools

**Descripción:** Herramientas para crear aplicaciones multiplataforma para iOS, Android y Windows con C# y F#.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.6.27406.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinos y tareas de compilación de NuGet | 15.9.28016.0 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.6.27309.0 | Obligatorio
Component.Android.SDK25 | Instalación de Android SDK (nivel de API 25) | 15.9.28107.0 | Optional
Component.OpenJDK | Distribución de Microsoft OpenJDK | 15.9.28125.51 | Optional

## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | nombre | Versión
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | SDK de TypeScript 2.0 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | SDK de TypeScript 2.1 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | SDK de TypeScript 2.2 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.3 | SDK de TypeScript 2.3 | 15.8.27729.1
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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Build Tools para Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017#build-tools-for-visual-studio-2017)
* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)
