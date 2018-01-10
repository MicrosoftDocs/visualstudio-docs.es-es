---
title: Identificadores de componente y carga de trabajo de Visual Studio Desktop Express 2017 | Microsoft Docs
description: "Uso de identificadores de componente y carga de trabajo para instalar Visual Studio mediante la línea de comandos o especificarlo como una dependencia en un manifiesto VSIX"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 12/01/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-acquisition
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.workload: multiple
ms.openlocfilehash: a628d2af0ccfaf66c936b391a977a0869139c98b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-desktop-express-2017-workload-and-component-ids"></a>Identificadores de componente y carga de trabajo de Visual Studio Desktop Express 2017

Las tablas de esta página presentan los identificadores que puede usar para instalar Visual Studio mediante la línea de comandos o que puede especificar como una dependencia en un manifiesto VSIX. Tenga en cuenta que agregaremos componentes adicionales a medida que se publiquen actualizaciones de Visual Studio.

Tenga en cuenta también lo siguiente sobre la página:

* Cada carga de trabajo tiene su propia sección, seguida por el identificador de la carga de trabajo y una tabla de los componentes que están disponibles para la carga de trabajo.
* De forma predeterminada, los componentes con carácter **Obligatorio** se instalarán cuando se instala la carga de trabajo. Si lo desea, también puede instalar los componentes con la marca **Recomendado** y **Opcional**.
* También hemos agregado una sección que muestra los componentes adicionales que no están asociados a ninguna carga de trabajo.

Al establecer las dependencias del manifiesto de VSIX, debe especificar solo identificadores de componentes. Utilice las tablas de esta página para determinar las dependencias de componente mínimas. En algunos casos, esto podría significar que se especifique solo un componente de una carga de trabajo. En otros escenarios, puede significar que especifique varios componentes de una sola carga de trabajo o varios componentes de varias cargas de trabajo. Para obtener más información, consulte la página [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Migración de proyectos de extensibilidad a Visual Studio 2017).

Para obtener más información acerca de cómo utilizar estos identificadores, vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Y, para obtener una lista de los identificadores de componente y carga de trabajo para otros productos, consulte la página [Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md) (Identificadores de componente y carga de trabajo de Visual Studio 2017).

## <a name="express-for-windows-desktop"></a>Express para escritorio de Windows

**Id.:** Microsoft.VisualStudio.Workload.WDExpress

**Descripción:** cree aplicaciones nativas y administradas como WPF, WinForms y Win32 con edición de código compatible con la sintaxis, control de código fuente y administración de elementos de trabajo. Incluye compatibilidad con C#, Visual Basic y Visual C++.

### <a name="components-included-by-this-workload"></a>Componentes incluidos en esta carga de trabajo

Id. de componente | nombre | Versión | Tipo de dependencia
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publicación de ClickOnce | 15.0.27019.1 | Obligatorio
Microsoft.Component.HelpViewer | Visor de Ayuda | 15.0.27005.2 | Obligatorio
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Obligatorio
Microsoft.Component.VC.Runtime.OSSupport | Tiempo de ejecución de Visual C++ para UWP | 15.0.27019.1 | Obligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.1 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5.2 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.5.TargetingPack | Paquete de compatibilidad de .NET Framework 4.5 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6.1 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.6.TargetingPack | Paquete de compatibilidad de .NET Framework 4.6 | 15.0.26621.2 | Obligatorio
Microsoft.Net.Component.4.TargetingPack | Paquete de compatibilidad de .NET Framework 4 | 15.0.26621.2 | Obligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Herramientas de desarrollo de .NET Framework 4.6.1 | 15.0.27005.2 | Obligatorio
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Herramientas de desarrollo de .NET Framework 4 – 4.6 | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Herramientas de conectividad y de publicación | 1.10.50912.1 | Obligatorio
Microsoft.VisualStudio.Component.CoreEditor | Editor de núcleo de Visual Studio | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.EntityFramework | Herramientas de Entity Framework 6 | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.NuGet | Administrador de paquetes de NuGet | 15.0.27128.1 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores de C# y Visual Basic Roslyn | 15.0.27019.1 | Obligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# y Visual Basic | 15.0.27019.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Entorno de tiempo de ejecución de SQL ADAL | 15.0.26606.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de datos CLR para SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | Utilidades de la línea de comandos de SQL Server | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Orígenes de datos para el soporte de SQL Server | 15.0.26621.2 | Obligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26919.1 | Obligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26906.1 | Obligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Herramientas de análisis estático | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.TextTemplating | Transformación de plantilla de texto | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.VC.CLI.Support | Compatibilidad con C++/CLI | 15.0.27019.1 | Obligatorio
Microsoft.VisualStudio.Component.VC.Tools.ARM | Bibliotecas y compiladores de Visual Studio C++ para ARM | 15.0.27019.1 | Obligatorio
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Bibliotecas y compiladores de Visual C++ para ARM64 | 15.0.27019.1 | Obligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Referencias de servicio y orígenes de datos | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK de Windows 10 (10.0.14393.0) | 15.0.26208.0 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK de Windows 10 (10.0.16299.0) para escritorio C++ [x86 and x64] | 15.0.27128.1 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | SDK de Windows 10 SDK (10.0.16299.0) para escritorio C++ [ARM y ARM64] | 15.0.27128.1 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK de Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27128.1 | Obligatorio
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK de Windows 10 (10.0.16299.0) para UWP: C++ | 15.0.27128.1 | Obligatorio

## <a name="unaffiliated-components"></a>Componentes no afiliados

Estos son componentes que no están incluidos en ninguna carga de trabajo, pero que pueden seleccionarse como un componente individual.

Id. de componente | nombre | Versión
--- | --- | ---
N/D | N/D | N/D

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)
