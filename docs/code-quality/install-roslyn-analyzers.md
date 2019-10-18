---
title: Instalar analizadores de Roslyn
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b86ab80e98b7e9609576002c4682bf01c388cd1d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445832"
---
# <a name="install-net-compiler-platform-code-analyzers"></a>Instalar .NET Compiler Platform analizadores de código

Visual Studio incluye un conjunto básico de analizadores de .NET Compiler Platform (*Roslyn*). Estos analizadores siempre están activados. Puede instalar analizadores adicionales como paquetes NuGet o como extensiones de Visual Studio en archivos *VSIX* .

## <a name="to-install-nuget-analyzer-packages"></a>Para instalar paquetes del analizador de NuGet

1. Busque el paquete de analizador que desea instalar en www.nuget.org.

   Por ejemplo, puede que desee [instalar los analizadores de Microsoft FxCop](install-fxcop-analyzers.md#nuget-package) para comprobar el código en busca de problemas de seguridad y rendimiento, entre otros. O bien, instale [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/) para buscar problemas de estilo en el código base.

2. Instale el paquete en Visual Studio, mediante la [consola del administrador de paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o la interfaz de usuario del administrador de [paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La página www.nuget.org de cada paquete de analizador muestra el comando para pegar en la **consola del administrador de paquetes**. Hay incluso un botón práctico para copiar el texto en el portapapeles.

   Los ensamblados del analizador se instalan y aparecen en **Explorador de soluciones** en **referencias**  > **analizadores**.

## <a name="to-install-vsix-analyzers"></a>Para instalar analizadores VSIX

::: moniker range="vs-2017"

1. En Visual Studio, seleccione **herramientas** > **extensiones y actualizaciones**.

   Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

   > [!NOTE]
   > Como alternativa, puede buscar y descargar la extensión del analizador directamente desde [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, seleccione **extensiones** > **administrar extensiones**.

   Se abre el cuadro de diálogo **administrar extensiones** .

   > [!NOTE]
   > Como alternativa, puede buscar y descargar la extensión del analizador directamente desde [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. Expanda en **línea** en el panel izquierdo y, a continuación, seleccione **Visual Studio Marketplace**.

3. En el cuadro de búsqueda, escriba el nombre de la extensión del analizador que desea instalar. Por ejemplo, puede que desee [instalar los analizadores de Microsoft FxCop](install-fxcop-analyzers.md#vsix) para comprobar el código en busca de problemas de seguridad y rendimiento, entre otros.

4. Seleccione **Descargar**.

   La extensión se descarga.

5. Seleccione **Aceptar** para cerrar el cuadro de diálogo y, a continuación, cierre todas las instancias de Visual Studio para iniciar el **instalador de VSIX**.

   Se abre el cuadro de diálogo **instalador de VSIX** .

   ![Instalador de VSIX para análisis de código de Microsoft](media/vsix-installer-code-analysis.png)

6. Seleccione **modificar** para iniciar la instalación.

7. Después de un minuto o dos, se completa la instalación. Seleccione **Cerrar**.

8. Abra Visual Studio de nuevo.

::: moniker range="vs-2017"

Si desea comprobar si la extensión está instalada, seleccione **herramientas**  > **extensiones y actualizaciones**. En el cuadro de diálogo **extensiones y actualizaciones** , seleccione la categoría **instalado** a la izquierda y, a continuación, busque la extensión por nombre.

::: moniker-end

::: moniker range=">=vs-2019"

Si desea comprobar si la extensión está instalada, seleccione **extensiones**  > **administrar extensiones**. En el cuadro de diálogo **administrar extensiones** , seleccione la categoría **instalado** a la izquierda y, a continuación, busque la extensión por nombre.

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Uso de analizadores de código en Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de código en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Instalar analizadores de FxCop](../code-quality/install-fxcop-analyzers.md)
