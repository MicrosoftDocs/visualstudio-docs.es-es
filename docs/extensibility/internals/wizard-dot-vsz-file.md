---
title: Asistente (. Vsz) File | Microsoft Docs
description: Obtenga información sobre los archivos .vsz que usa el IDE para iniciar asistentes. Los archivos contienen información sobre a qué asistente llamar y qué pasar al asistente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de687dae79fa1613090fb400f73ab658ee5d66cb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900660"
---
# <a name="wizard-vsz-file"></a>Archivo de asistente (.Vsz)

El entorno de desarrollo integrado (IDE) usa archivos .vsz para iniciar asistentes. Estos archivos .vsz contienen información que el IDE usa para determinar a qué asistente llamar y qué información se va a pasar al asistente.

Un archivo .vsz es una versión de un .ini de texto con formato de archivo que no tiene secciones. La información conocida por el IDE se almacena al principio del archivo. Esto proporciona un vínculo entre el asistente al que llama el IDE y los parámetros que se encuentran en el archivo .vsz que se van a pasar al IDE. El resto del archivo proporciona parámetros que son específicos del asistente y que el IDE va a recopilar y pasar al asistente específico.

En el ejemplo siguiente se muestra el contenido de un archivo .vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

A continuación se encuentran las partes del archivo .vsz.

|Parte|Descripción|
|----------|-----------------|
|VSWizard|El primer parámetro del archivo es el número de versión del formato de archivo de plantilla. Este número de versión debe ser 6.0, 7.0, 7.1 u 8.0. No se pueden iniciar otros números y provocar un error de formato no válido.|
|Asistente|Este campo contiene el ProgID OLE del asistente o, como alternativa, una representación de cadena GUID del CLSID del asistente que el IDE crea de forma cocreada.|
|Parámetro|Estas partes son opcionales. Puede agregar tantas como sea necesario.|

Los parámetros permiten que el archivo .vsz pase parámetros personalizados adicionales al asistente. Cada valor se pasa como un elemento de cadena en una matriz de variantes al asistente. Para obtener más información, vea [Parámetros personalizados.](../../extensibility/internals/custom-parameters.md)

Para agregar un identificador de configuración regional predeterminado al archivo .vsz, especifique =xxxx, donde xxxx es el identificador de configuración regional, por `FALLBACK_LCID` ejemplo, 1033 para inglés. Cuando se define el parámetro , el asistente usa el identificador de configuración regional de reserva proporcionado si no se encuentra `FALLBACK_LCID` el identificador actual.

## <a name="see-also"></a>Consulta también

- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
