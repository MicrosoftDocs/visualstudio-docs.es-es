---
title: Instalar analizadores de FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9791e2dbb6d4a82a49539216eda53d217140bd52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649335"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Instalar analizadores de FxCop en Visual Studio

Microsoft creó un conjunto de analizadores, denominado [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), que contiene las reglas de "FxCop" más importantes del análisis heredado. Estos analizadores comprueban el código en busca de problemas de seguridad, rendimiento y diseño, entre otros.

Puede instalar estos analizadores FxCop como un paquete NuGet o como una extensión VSIX en Visual Studio. Para obtener información sobre las ventajas y desventajas de cada uno, vea [paquete NuGet frente a extensión VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Detección de

::: moniker range=">=vs-2019"

En la versión 16,3 de Visual Studio 2019 y versiones posteriores, puede instalar el paquete NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) directamente desde la página Propiedades de análisis de código del proyecto:

1. Haga clic con el botón secundario en el nodo del proyecto en **Explorador de soluciones**, seleccione **propiedades**y, a continuación, seleccione la pestaña **análisis de código** .

   ![Instalar el paquete de analizadores de FxCop desde la página Propiedades de Visual Studio](media/install-fxcop-properties-page.png)

2. Haga clic en **Instalar**.

   Visual Studio instala la versión más reciente del paquete Microsoft. CodeAnalyzers. FxCopAnalyzers. Los ensamblados aparecen en **Explorador de soluciones** en **referencias**  > **analizadores**.

   ![Nodo analizadores en Explorador de soluciones](media/solution-explorer-analyzers-node.png)

Si usa una versión anterior de Visual Studio 2019, instale el paquete mediante la [consola del administrador de paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o la interfaz de usuario del administrador de [paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. [Determine qué versión del paquete de analizador](#fxcopanalyzers-package-versions) desea instalar, en función de su versión de Visual Studio.

2. Instale el paquete en Visual Studio mediante la [consola del administrador de paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o la interfaz de usuario del administrador de [paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La página nuget.org de cada paquete de analizador muestra el comando para pegar en la **consola del administrador de paquetes**. Hay incluso un botón práctico para copiar el texto en el portapapeles.
   >
   > ![Página de NuGet.org que muestra el comando consola del administrador de paquetes](media/nuget-package-manager-command.png)

   Los ensamblados del analizador se instalan y aparecen en **Explorador de soluciones** en **referencias** > **analizadores**.

::: moniker-end

### <a name="custom-installation"></a>Instalación personalizada

Para la instalación personalizada, por ejemplo, para especificar una versión diferente del paquete, seleccione el botón de puntos suspensivos (...) de la página Propiedades de análisis de código del proyecto. Este botón abre el administrador de paquetes NuGet con "Microsoft. CodeAnalysis. FxCopAnalyzers" como cadena de búsqueda.

![Instalar el paquete de analizadores de FxCop personalizados en la página Propiedades de Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Determine [qué versión del paquete de analizador](#fxcopanalyzers-package-versions) desea instalar, en función de su versión de Visual Studio. También puede instalar el paquete desde la [interfaz de usuario del administrador de paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Versiones del paquete FxCopAnalyzers

Utilice las siguientes directrices para determinar qué versión del paquete de analizadores de FxCop instalar para su versión de Visual Studio:

| Versión de Visual Studio | Versión del paquete de analizador de FxCop |
| - | - |
| Visual Studio 2019 (todas las versiones)<br />Visual Studio 2017 versión 15,8 y versiones posteriores | [avanzada](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 versión 15,5 a 15,7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 versión 15,3 a 15,4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 versión 15,0 a 15,2 | [2.0.0: beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 Update 2 y 3 | [1.2.0: beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

En la versión 15,5 de Visual Studio 2017 y versiones posteriores, puede instalar la extensión [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) que contiene todos los analizadores de FxCop para proyectos administrados.

1. En Visual Studio, seleccione **herramientas** > **extensiones y actualizaciones**.

   Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

   > [!NOTE]
   > También puede descargar la extensión directamente desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Expanda en **línea** en el panel izquierdo y, a continuación, seleccione **Visual Studio Marketplace**.

3. En el cuadro de búsqueda, escriba "Análisis de código" y busque la extensión **Microsoft Code analysis 2017** .

   ![Extensión de análisis de código de Microsoft 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

La extensión [análisis de código de Microsoft 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) contiene todos los analizadores de FxCop para proyectos administrados. Para instalar esta extensión:

1. En Visual Studio, seleccione **extensiones** > **administrar extensiones**.

   Se abre el cuadro de diálogo **administrar extensiones** .

   > [!NOTE]
   > También puede descargar la extensión directamente desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Expanda en **línea** en el panel izquierdo y, a continuación, seleccione **Visual Studio Marketplace**.

3. En el cuadro de búsqueda, escriba "Análisis de código" y busque la extensión **Microsoft Code analysis 2019** .

   ![Extensión de análisis de código de Microsoft 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Seleccione **Descargar**.

   La extensión se descarga.

5. Seleccione **Aceptar** para cerrar el cuadro de diálogo y, a continuación, cierre todas las instancias de Visual Studio para iniciar el **instalador de VSIX**.

   Se abre el cuadro de diálogo **instalador de VSIX** .

   ::: moniker range="vs-2017"

   ![Instalador de VSIX para análisis de código de Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Seleccione **modificar** para iniciar la instalación.

   Después de un minuto o dos, se completa la instalación.

7. Seleccione **cerrar**y, a continuación, vuelva a abrir Visual Studio.

::: moniker range="vs-2017"

Si desea comprobar si la extensión está instalada, seleccione **herramientas**  > **extensiones y actualizaciones**. En el cuadro de diálogo **extensiones y actualizaciones** , seleccione la categoría **instalado** a la izquierda y, a continuación, busque la extensión por nombre.

::: moniker-end

::: moniker range=">=vs-2019"

Si desea comprobar si la extensión está instalada, seleccione **extensiones**  > **administrar extensiones**. En el cuadro de diálogo **administrar extensiones** , seleccione la categoría **instalado** a la izquierda y, a continuación, busque la extensión por nombre.

::: moniker-end

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de código en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Uso de analizadores de código en Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migración de análisis heredado a analizadores de código](../code-quality/fxcop-analyzers.yml)
