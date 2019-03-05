---
title: Solución de problemas de detección de plantillas en Visual Studio | Documentos de Microsoft
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9ae6220ac38de7bf2edc7b5c305ecb377a46f18
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324005"
---
# <a name="troubleshooting-template-installation"></a>Solución de problemas de instalación de la plantilla

Si experimenta problemas al implementar las plantillas de proyecto o elemento, puede habilitar el registro de diagnóstico.

::: moniker range="vs-2017"

1. Cree un archivo pkgdef en el *Common7\IDE\CommonExtensions* carpeta para la instalación. Por ejemplo, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Cree un archivo pkgdef en el *Common7\IDE\CommonExtensions* carpeta para la instalación. Por ejemplo, *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. En el archivo pkgdef, agregue lo siguiente:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Abra un [símbolo](/dotnet/framework/tools/developer-command-prompt-for-vs) para la instalación y ejecución `devenv /updateConfiguration`.

::: moniker range="vs-2017"

4. Iniciar Visual Studio y los cuadros de diálogo nuevo proyecto y el nuevo elemento para inicializar ambos árboles de plantilla.

   El registro de plantilla aparece ahora en **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid se corresponde con el identificador de instalación de la instancia de Visual Studio). La inicialización de cada árbol de la plantilla anexa entradas en este registro.

::: moniker-end

::: moniker range=">=vs-2019"

4. Iniciar Visual Studio y los cuadros de diálogo nuevo proyecto y el nuevo elemento para inicializar ambos árboles de plantilla.

   El registro de plantilla aparece ahora en **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid se corresponde con el identificador de instalación de la instancia de Visual Studio). La inicialización de cada árbol de la plantilla anexa entradas en este registro.

::: moniker-end

El archivo de registro contiene las columnas siguientes:

- **FullPathToTemplate**, que tiene los siguientes valores:

    - 1 para la implementación basada en manifiesto

    - 0 para la implementación basada en disco

- **TemplateFileName**

- Otras propiedades de plantilla

> [!NOTE]
> Para deshabilitar el registro, quite el archivo pkgdef o cambie el valor de `EnableTemplateDiscoveryLog` a `dword:00000000`y, a continuación, ejecute `devenv /updateConfiguration` nuevo.

## <a name="see-also"></a>Vea también

- [Creación de plantillas de proyecto y elemento personalizadas](creating-custom-project-and-item-templates.md)