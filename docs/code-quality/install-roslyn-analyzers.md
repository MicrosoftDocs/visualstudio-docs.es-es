---
title: Instalar analizadores de terceros
ms.date: 08/27/2020
description: Obtenga información sobre cómo instalar analizadores de terceros en Visual Studio. Vea cómo instalar analizadores en archivos. vsix y paquetes del analizador de NuGet.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 93cd01c0a90f2864843549c3ce11e066a16a8843
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040386"
---
# <a name="install-third-party-analyzers"></a>Instalación de analizadores de terceros

Visual Studio incluye un conjunto básico de analizadores de .NET Compiler Platform (*Roslyn*). Estos analizadores siempre están activados. Puede instalar analizadores adicionales como paquetes NuGet o como extensiones de Visual Studio en archivos *VSIX* .

## <a name="to-install-nuget-analyzer-packages"></a>Para instalar paquetes del analizador de NuGet

1. Busque el paquete de analizador que desea instalar en www.nuget.org.

   Por ejemplo, puede que desee instalar [StyleCop. analizadores](https://www.nuget.org/packages/stylecop.analyzers/) para buscar problemas de estilo en el código base.

2. Instale el paquete en Visual Studio, mediante la [consola del administrador de paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) o la interfaz de usuario del administrador de [paquetes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > La página www.nuget.org de cada paquete de analizador muestra el comando para pegar en la **consola del administrador de paquetes**. Hay incluso un botón práctico para copiar el texto en el portapapeles.

   Los ensamblados del analizador se instalan y aparecen en **Explorador de soluciones** en **References**  >  **analizadores** de referencias.

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

3. En el cuadro de búsqueda, escriba el nombre de la extensión del analizador que desea instalar.

4. Seleccione **Descargar**.

   La extensión se descarga.

5. Seleccione **Aceptar** para cerrar el cuadro de diálogo y, a continuación, cierre todas las instancias de Visual Studio para iniciar el **instalador de VSIX**.

   Se abre el cuadro de diálogo **instalador de VSIX** .

   ![Instalador de VSIX para análisis de código de Microsoft](media/vsix-installer-code-analysis.png)

6. Seleccione **modificar** para iniciar la instalación.

7. Después de un minuto o dos, se completa la instalación. Seleccione **Cerrar**.

8. Abra Visual Studio de nuevo.

::: moniker range="vs-2017"

Si desea comprobar si la extensión está instalada, seleccione **herramientas**  >  **extensiones y actualizaciones**. En el cuadro de diálogo **extensiones y actualizaciones** , seleccione la categoría **instalado** a la izquierda y, a continuación, busque la extensión por nombre.

::: moniker-end

::: moniker range=">=vs-2019"

Si desea comprobar si la extensión está instalada, seleccione **extensiones**  >  **administrar extensiones**. En el cuadro de diálogo **administrar extensiones** , seleccione la categoría **instalado** a la izquierda y, a continuación, busque la extensión por nombre.

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Uso de analizadores de código en Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de código en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Instalar analizadores de .NET](../code-quality/install-net-analyzers.md)
