---
title: Instalar analizadores de FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508776"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Instalar analizadores FxCop en Visual Studio

Microsoft creó un conjunto de analizadores, [denominados Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), que contiene las reglas "FxCop" más importantes del análisis heredado. Estos analizadores comprueban el código en busca de problemas de seguridad, rendimiento y diseño, entre otros.

Puede instalar estos analizadores FxCop como un paquete NuGet o como una extensión VSIX a Visual Studio. Para obtener información sobre los pros y los contras de cada uno, vea [NuGet package vs.](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)

## <a name="nuget-package"></a>Paquete de NuGet

::: moniker range=">=vs-2019"

En Visual Studio 2019 versión 16.3 y versiones posteriores, puede instalar el paquete NuGet [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) directamente desde la página de propiedades análisis de código del proyecto:

1. Haga clic con el botón secundario en el nodo del proyecto en el **Explorador**de soluciones , seleccione **Propiedades**y, a continuación, seleccione la pestaña **Análisis** de código.

   ![Instalar el paquete de analizadores de FxCop desde la página de propiedades en Visual Studio](media/install-fxcop-properties-page.png)

2. Seleccione **Instalar**.

   Visual Studio instala la versión más reciente del paquete Microsoft.CodeAnalysis.FxCopAnalyzers. Los ensamblados aparecen en el Explorador de **soluciones** en**Analizadores de** **referencias** > .

   ![Nodo Analizadores en el Explorador de soluciones](media/solution-explorer-analyzers-node.png)

Si usa una versión anterior de Visual Studio 2019, instale el paquete mediante la consola del Administrador de [paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o la interfaz de usuario del Administrador de [paquetes.](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)

::: moniker-end

::: moniker range="vs-2017"

1. [Determine qué versión](#fxcopanalyzers-package-versions) del paquete del analizador instalar, en función de la versión de Visual Studio.

2. Instale el paquete en Visual Studio mediante la consola del Administrador de [paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o la [interfaz](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)de usuario del Administrador de paquetes.

   > [!NOTE]
   > La página nuget.org de cada paquete de analizador muestra el comando que se debe pegar en la consola del Administrador de **paquetes.** Incluso hay un práctico botón para copiar el texto en el portapapeles.
   >
   > ![NuGet.org página que muestra el comando de la consola del Administrador de paquetes](media/nuget-package-manager-command.png)

   Los ensamblados del analizador están instalados y aparecen en el **Explorador** de soluciones en **Analizadores de** **referencias** > .

::: moniker-end

### <a name="custom-installation"></a>Instalación personalizada

Para la instalación personalizada, por ejemplo, para especificar una versión diferente del paquete, seleccione el botón de puntos suspensivos (...) en la página de propiedades análisis de código del proyecto. Este botón abre el administrador de paquetes NuGet con "Microsoft.CodeAnalysis.FxCopAnalyzers" como cadena de búsqueda.

![Instalar el paquete de analizadores FxCop personalizadodesde desde la página de propiedades en Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Determine [qué versión](#fxcopanalyzers-package-versions) del paquete del analizador instalar, en función de la versión de Visual Studio. También puede instalar el paquete desde la [interfaz](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)de usuario del Administrador de paquetes.

### <a name="fxcopanalyzers-package-versions"></a>Versiones de paquetes FxCopAnalyzers

Use las siguientes directrices para determinar qué versión del paquete de analizadores de FxCop se va a instalar para la versión de Visual Studio:

| Versión de Visual Studio | Versión del paquete del analizador FxCop |
| - | - |
| Visual Studio 2019 (todas las versiones)<br />Visual Studio 2017 versión 15.8 y versiones posteriores | [Últimos](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 versión 15.5 a 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 versión 15.3 a 15.4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 versión 15.0 a 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 actualización 2 y 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

En Visual Studio 2017 versión 15.5 y versiones posteriores, puede instalar la extensión [de Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) que contiene todos los analizadores de FxCop para proyectos administrados.

1. En Visual Studio, seleccione **Extensiones y actualizaciones**de **herramientas** > .

   Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

   > [!NOTE]
   > Como alternativa, descargue la extensión directamente desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Expanda **En línea** en el panel izquierdo y, a continuación, seleccione Visual Studio **Marketplace**.

3. En el cuadro de búsqueda, escriba "análisis de código" y busque la extensión **Microsoft Code Analysis 2017.**

   ![Extensión de Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

La extensión [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) contiene todos los analizadores FxCop para proyectos administrados. Para instalar esta extensión:

1. En Visual Studio, seleccione **Extensiones** > **administrar extensiones**.

   Se abre el cuadro de diálogo **Administrar extensiones.**

   > [!NOTE]
   > Como alternativa, descargue la extensión directamente desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Expanda **En línea** en el panel izquierdo y, a continuación, seleccione Visual Studio **Marketplace**.

3. En el cuadro de búsqueda, escriba "análisis de código" y busque la extensión **Microsoft Code Analysis 2019.**

   ![Extensión de Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Seleccione **Descargar**.

   La extensión se descarga.

5. Seleccione **Aceptar** para cerrar el cuadro de diálogo y, a continuación, cierre todas las instancias de Visual Studio para iniciar el **instalador de VSIX**.

   Se abre el cuadro de diálogo **Instalador de VSIX.**

   ::: moniker range="vs-2017"

   ![Instalador VSIX para Microsoft Code Analysis](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Seleccione **Modificar** para iniciar la instalación.

   Después de uno o dos minutos, la instalación se completa.

7. Seleccione **Cerrar**y, a continuación, vuelva a abrir Visual Studio.

::: moniker range="vs-2017"

Si desea comprobar si la extensión está instalada, **seleccione** > **Extensiones y actualizaciones**de herramientas . En el cuadro de diálogo **Extensiones y actualizaciones,** seleccione la categoría **Instalado** a la izquierda y, a continuación, busque la extensión por nombre.

::: moniker-end

::: moniker range=">=vs-2019"

Si desea comprobar si la extensión está instalada, seleccione **Extensiones** > **de administración de extensiones**. En el cuadro de diálogo **Administrar extensiones,** seleccione la categoría **Instalado** a la izquierda y, a continuación, busque la extensión por nombre.

::: moniker-end

## <a name="see-also"></a>Consulte también

- [Descripción general de los analizadores de código en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Uso de analizadores de código en Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrar del análisis heredado a los analizadores de código](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
