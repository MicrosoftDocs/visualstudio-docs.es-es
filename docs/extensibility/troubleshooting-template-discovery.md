---
title: Solución de problemas de detección de plantillas en Visual Studio | Documentos de Microsoft
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39ebb7c49e5a8482ab0b2ef5c3a5257d0237b39c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836158"
---
# <a name="troubleshooting-template-installation"></a>Solución de problemas de instalación de la plantilla

Si experimenta problemas al implementar las plantillas de proyecto o elemento, puede habilitar el registro de diagnóstico.

1. Cree un archivo pkgdef en la carpeta Common7\IDE\CommonExtensions para la instalación (por ejemplo, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) con el siguiente contenido:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Abra una "línea de comandos de desarrollador" para la instalación mediante una búsqueda en búsqueda de Windows y ejecute `devenv /updateConfiguration`.

1. Iniciar Visual Studio y los cuadros de diálogo nuevo proyecto y el nuevo elemento para inicializar ambos árboles de plantilla. El registro de plantilla aparece ahora en **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid se corresponde con el identificador de instalación de la instancia de Visual Studio). La inicialización de cada árbol de la plantilla anexa entradas en este registro.

El archivo de registro contiene las columnas siguientes:

- **FullPathToTemplate**, que tiene los siguientes valores:

    - 1 para la implementación basada en manifiesto

    - 0 para la implementación basada en disco

- **TemplateFileName**

- Otras propiedades de plantilla

> [!NOTE]
> Para deshabilitar el registro, quite el archivo pkgdef o cambie el valor de `EnableTemplateDiscoveryLog` a `dword:00000000`y, a continuación, ejecute `devenv /updateConfiguration` nuevo.

## <a name="see-also"></a>Vea también

[Creación de plantillas de proyecto y elemento personalizadas](creating-custom-project-and-item-templates.md)