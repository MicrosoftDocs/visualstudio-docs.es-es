---
title: Instalar analizadores de Roslyn en Visual Studio
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8a3b40b3b471e6bb57da561ac51f23086a0f01bd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="install-net-compiler-platform-analyzers"></a>Instalar analizadores de .NET Compiler Platform

2017 de Visual Studio incluye un conjunto básico de .NET Compiler Platform (*Roslyn*) analizadores. Estos analizadores están siempre activadas. Puede instalar analizadores adicionales como paquetes de NuGet, o extensiones de Visual Studio en *VSIX* archivos.

## <a name="to-install-nuget-package-analyzers"></a>Para instalar analizadores de paquetes de NuGet

1. [Determinar qué versión del paquete analizador](https://github.com/dotnet/roslyn-analyzers#recommended-version-of-analyzer-packages) instalar, según la versión de Visual Studio.

1. Instalar el paquete en Visual Studio, mediante el [Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o [UI del Administrador de paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La página de nuget.org para cada paquete de analizador muestra el comando Pegar en el **Package Manager Console**. Incluso es un botón útil para copiar el texto en el Portapapeles.
   >
   > ![Página de NuGet.org que muestra comandos de consola de administrador de paquetes](media/nuget-package-manager-command.png)

   Los ensamblados de analizador están instalados y aparecen en **el Explorador de soluciones** en **referencias** > **analizadores**.

   ![Nodo de analizadores en el Explorador de soluciones](media/solution-explorer-analyzers-node.png)

## <a name="to-install-vsix-analyzers"></a>Para instalar analizadores VSIX

1. En Visual Studio, seleccione **herramientas** > **extensiones y actualizaciones**.

   Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

   > [!NOTE]
   > O bien, descargue la extensión directamente desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Expanda **en línea** en el panel izquierdo y, a continuación, seleccione **Visual Studio Marketplace**.

1. En el cuadro de búsqueda, escriba "análisis de código" y busque el **2017 de análisis de código de Microsoft** extensión.

   ![Extensión de análisis de código de Microsoft](media/extensions-and-updates-code-analysis.png)

1. Seleccione **descargar**.

   Descargar la extensión.

1. Seleccione **Aceptar** para cerrar el cuadro de diálogo y, a continuación, cierre todas las instancias de Visual Studio para iniciar la **instalador VSIX**.

   El **instalador VSIX** abre el cuadro de diálogo.

   ![Instalador VSIX para el análisis de código de Microsoft](media/vsix-installer-code-analysis.png)

1. Seleccione **modificar** para iniciar la instalación.

1. Después de un minuto o dos, se completa la instalación. Seleccione **cerrar**.

1. Vuelva a abrir Visual Studio.

Si desea comprobar si la extensión está instalada, seleccione **herramientas** > **extensiones y actualizaciones**. En el **extensiones y actualizaciones** cuadro de diálogo, seleccione la **instalado** categoría de la izquierda y, a continuación, busque la extensión por su nombre.

## <a name="next-steps"></a>Pasos siguientes

- [Usar los analizadores de Roslyn de Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de Roslyn en Visual Studio](../code-quality/roslyn-analyzers-overview.md)