---
title: Instalar analizadores de FxCop
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7690d1c67797c3a13dc22364d93d8af686e4f90c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892056"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Instalar analizadores de FxCop en Visual Studio

Microsoft creó un conjunto de analizadores, llamado [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), que contiene las reglas de "FxCop" más importante del análisis de código estático, puede convertida en analizadores de Roslyn. Estos analizadores comprobación el código de seguridad, rendimiento y problemas de diseño, entre otros.

Puede instalar estos analizadores de FxCop como un paquete de NuGet o como una extensión VSIX a Visual Studio. Para obtener información acerca de las ventajas y desventajas de cada uno, consulte [frente a paquetes de NuGet. Extensión de VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>Para instalar analizadores de FxCop como un paquete de NuGet

1. [Determinar qué versión del paquete de analizador](#fxcopanalyzers-package-versions) instalar, según la versión de Visual Studio.

2. Instale el paquete en Visual Studio, ya sea mediante el [Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o [UI del Administrador de paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La página de nuget.org para cada paquete del analizador muestra el comando Pegar en el **Package Manager Console**. Incluso hay un botón útil para copiar el texto en el Portapapeles.
   >
   > ![Página de NuGet.org que muestra comandos de consola de administrador de paquetes](media/nuget-package-manager-command.png)

   Los ensamblados del analizador se instalan y aparecen en **el Explorador de soluciones** en **referencias** > **analizadores**.

   ![Nodo de analizadores en el Explorador de soluciones](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Versiones del paquete FxCopAnalyzers

Utilice las siguientes directrices para determinar qué versión del paquete de analizadores de FxCop para instalar su versión de Visual Studio:

| Versión de Visual Studio | Versión del paquete de analizador de FxCop |
| - | - |
| Visual Studio 2017 versión 15.5 y versiones posterior | 2.6.2, por ejemplo https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2 |
| Visual Studio 2017 versión 15.3 a 15.4 | 2.3.0-Beta1, por ejemplo https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1 |
| Visual Studio 2017 versión 15.0 a 15.2 | 2.0.0-Beta2, por ejemplo https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2 |
| Visual Studio 2015 update 2 y 3 | Versión 1.2.0-beta2, por ejemplo https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2 |
| Visual Studio 2015 Update 1 | La versión 1.1.0, por ejemplo https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1. |
| Visual Studio 2015 RTW | Versión 1.0.1, por ejemplo https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1 |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>Para instalar analizadores de FxCop como una extensión VSIX

En Visual Studio 2017 versión 15.5 y versiones posterior, puede instalar el [2017 de análisis de código de Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) extensión que contiene todos los analizadores de FxCop para proyectos administrados.

1. En Visual Studio, seleccione **herramientas** > **extensiones y actualizaciones**.

   Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

   > [!NOTE]
   > Como alternativa, descargue la extensión directamente desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Expanda **Online** en el panel izquierdo y, a continuación, seleccione **Visual Studio Marketplace**.

1. En el cuadro de búsqueda, escriba "análisis de código" y busque el **2017 de análisis de código de Microsoft** extensión.

   ![Extensión de análisis de código de Microsoft](media/extensions-and-updates-code-analysis.png)

1. Seleccione **descargar**.

   Descargar la extensión.

1. Seleccione **Aceptar** para cerrar el cuadro de diálogo y, a continuación, cierre todas las instancias de Visual Studio para iniciar el **instalador de VSIX**.

   El **instalador de VSIX** abre el cuadro de diálogo.

   ![Instalador de VSIX para el análisis de código de Microsoft](media/vsix-installer-code-analysis.png)

1. Seleccione **modificar** para iniciar la instalación.

1. Después de un minuto o dos, se completa la instalación. Seleccione **cerrar**.

1. Vuelva a abrir Visual Studio.

Si desea comprobar si la extensión está instalada, seleccione **herramientas** > **extensiones y actualizaciones**. En el **extensiones y actualizaciones** cuadro de diálogo, seleccione el **instalado** categoría de la izquierda y, a continuación, busque la extensión por nombre.

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de Roslyn en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Usar los analizadores de Roslyn en Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrar de FxCop para analizadores de Roslyn](../code-quality/fxcop-analyzers.yml)