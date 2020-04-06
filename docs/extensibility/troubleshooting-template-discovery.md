---
title: Solucionar problemas de detección de plantillas en Visual Studio ? Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698934"
---
# <a name="troubleshooting-template-installation"></a>Solución de problemas de instalación de plantillas

Si tiene problemas para implementar las plantillas de proyecto o elemento, puede habilitar el registro de diagnóstico.

::: moniker range="vs-2017"

1. Cree un archivo pkgdef en la carpeta *Common7-IDE-CommonExtensions* para la instalación. Por ejemplo, *C:-Archivos de programa (x86)-Microsoft Visual Studio-2017-Empresa-Common7-IDE-CommonExtensions-EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Cree un archivo pkgdef en la carpeta *Common7-IDE-CommonExtensions* para la instalación. Por ejemplo, *C:-Archivos de programa (x86)-Microsoft Visual Studio-2019-Empresa-Common7-IDE-CommonExtensions-EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Agregue lo siguiente al archivo pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Abra un símbolo del sistema `devenv /updateConfiguration`para [desarrolladores](/dotnet/framework/tools/developer-command-prompt-for-vs) para la instalación y ejecute .

::: moniker range="vs-2017"

4. Abra Visual Studio e inicie los cuadros de diálogo Nuevo proyecto y Nuevo elemento para inicializar ambos árboles de plantilla.

   El registro de la plantilla ahora aparece en **%LOCALAPPDATA%-Microsoft-VisualStudio-15.0_[instanceid]-VsTemplateDiagnosticsList.csv** (instanceid corresponde al identificador de instalación de la instancia de Visual Studio). Cada inicialización del árbol de plantillas anexa entradas a este registro.

::: moniker-end

::: moniker range=">=vs-2019"

4. Abra Visual Studio e inicie los cuadros de diálogo **Crear un nuevo proyecto** y Nuevo **elemento** para inicializar ambos árboles de plantilla.

   El registro de la plantilla ahora aparece en **%LOCALAPPDATA%-Microsoft-VisualStudio-16.0_[instanceid]-VsTemplateDiagnosticsList.csv** (instanceid corresponde al identificador de instalación de la instancia de Visual Studio). Cada inicialización del árbol de plantillas anexa entradas a este registro.

::: moniker-end

El archivo de registro contiene las siguientes columnas:

- **FullPathToTemplate**, que tiene los siguientes valores:

  - 1 para la implementación basada en manifiestos

  - 0 para la implementación basada en disco

- **TemplateFileName**

- Otras propiedades de plantilla

> [!NOTE]
> Para deshabilitar el registro, quite el archivo pkgdef o cambie el valor de `EnableTemplateDiscoveryLog` a y, a continuación, vuelva a `dword:00000000`ejecutarlo. `devenv /updateConfiguration`

## <a name="see-also"></a>Vea también

- [Creación de plantillas de proyectos y elementos personalizadas](creating-custom-project-and-item-templates.md)
