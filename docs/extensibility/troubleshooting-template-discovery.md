---
title: Solución de problemas de detección de plantillas en Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo habilitar el registro de diagnóstico para solucionar problemas de implementación de proyectos y plantillas personalizados en el SDK de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1ea99c1d74c06ab42ff86f07de4cf5c76e95de43
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151329"
---
# <a name="troubleshooting-template-installation"></a>Solución de problemas de instalación de plantillas

Si surgen problemas al implementar las plantillas de proyecto o elemento, puede habilitar el registro de diagnóstico.

::: moniker range="vs-2017"

1. Cree un archivo pkgdef en la carpeta *Common7\IDE\CommonExtensions* para su instalación. Por ejemplo, *c:\Archivos de programa (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Cree un archivo pkgdef en la carpeta *Common7\IDE\CommonExtensions* para su instalación. Por ejemplo, *c:\Archivos de programa (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Agregue lo siguiente al archivo pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Abra una [símbolo del sistema para desarrolladores](../ide/reference/command-prompt-powershell.md) para su instalación y ejecute `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Abra Visual Studio e inicie los cuadros de diálogo nuevo proyecto y nuevo elemento para inicializar ambos árboles de plantilla.

   El registro de plantilla aparece ahora en **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_ [InstanceID] \VsTemplateDiagnosticsList.csv** (InstanceID corresponde al identificador de instalación de la instancia de Visual Studio). Cada inicialización del árbol de plantillas anexa entradas a este registro.

::: moniker-end

::: moniker range=">=vs-2019"

4. Abra Visual Studio e inicie los cuadros de diálogo **crear un nuevo proyecto** y **nuevo elemento** para inicializar ambos árboles de plantillas.

   El registro de plantilla aparece ahora en **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_ [InstanceID] \VsTemplateDiagnosticsList.csv** (InstanceID corresponde al identificador de instalación de la instancia de Visual Studio). Cada inicialización del árbol de plantillas anexa entradas a este registro.

::: moniker-end

El archivo de registro contiene las siguientes columnas:

- **FullPathToTemplate**, que tiene los siguientes valores:

  - 1 para la implementación basada en manifiestos

  - 0 para la implementación basada en disco

- **TemplateFileName**

- Otras propiedades de la plantilla

> [!NOTE]
> Para deshabilitar el registro, quite el archivo pkgdef o cambie el valor de `EnableTemplateDiscoveryLog` a `dword:00000000` y, a continuación, vuelva a ejecutar `devenv /updateConfiguration` .

## <a name="see-also"></a>Consulte también

- [Crear plantillas de proyecto y de elemento personalizadas](creating-custom-project-and-item-templates.md)
- [Solucionar problemas de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
