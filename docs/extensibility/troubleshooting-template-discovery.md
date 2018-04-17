---
title: Solucionar problemas de detección de la plantilla en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d183fd664258fbb7dbcf27c913c56c6f6160e6c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-template-installation"></a>Solución de problemas de instalación de la plantilla

Si experimenta problemas de implementación de las plantillas de proyecto o un elemento, puede habilitar el registro de diagnóstico.

1. Cree un archivo pkgdef en la carpeta Common7\IDE\CommonExtensions para la instalación (por ejemplo, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) con el siguiente contenido:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Abra un "símbolo" para la instalación mediante una búsqueda en búsqueda de Windows y ejecute `devenv /updateConfiguration`.

1. Inicie Visual Studio e inicie los cuadros de diálogo nuevo proyecto y el nuevo elemento para inicializar dos árboles de plantilla. El registro de plantilla aparece ahora en **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid se corresponde con el identificador de instalación de la instancia de Visual Studio). La inicialización de árbol de cada plantilla anexa entradas para este registro.

El archivo de registro contiene las columnas siguientes:

- **FullPathToTemplate**, que tiene los siguientes valores:

    - 1 para la implementación basada en manifiestos

    - 0 para la implementación basada en disco

- **TemplateFileName**

- Otras propiedades de plantilla

> [!NOTE]
> Para deshabilitar el registro, quite el archivo pkgdef o cambie el valor de `EnableTemplateDiscoveryLog` a `dword:00000000`y, a continuación, ejecute `devenv /updateConfiguration` nuevo.

## <a name="see-also"></a>Vea también

[Crear plantillas de proyecto y de elementos personalizadas](creating-custom-project-and-item-templates.md)