---
title: Asistente (. Archivo vsz) | Microsoft Docs
description: Obtenga información sobre los archivos. vsz que usa el IDE para iniciar asistentes. Los archivos contienen información sobre qué asistente llamar y qué pasar al asistente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5fa9b9e06ccb20e6a2859770c0637fc85422fd0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935865"
---
# <a name="wizard-vsz-file"></a>Archivo de asistente (.Vsz)

El entorno de desarrollo integrado (IDE) utiliza archivos. vsz para iniciar asistentes. Estos archivos. vsz contienen información que el IDE usa para determinar a qué asistente se debe llamar y qué información se debe pasar al asistente.

Un archivo. vsz es una versión de un archivo de texto con formato. ini que no tiene secciones. La información que se conoce en el IDE se almacena al principio del archivo. Esto proporciona un vínculo entre el Asistente al que llama el IDE y los parámetros que se encuentran en el archivo. vsz que se van a pasar al IDE. El resto del archivo proporciona parámetros que son específicos del asistente y que se van a recopilar mediante el IDE y pasarse al asistente específico.

En el ejemplo siguiente se muestra el contenido de un archivo. vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

A continuación se indican las partes del archivo. vsz.

|Parte|Descripción|
|----------|-----------------|
|VSWizard|El primer parámetro del archivo es el número de versión del formato de archivo de plantilla. Este número de versión debe ser 6,0, 7,0, 7,1 o 8,0. No se pueden iniciar otros números y se producirá un error de formato no válido.|
|Asistente|Este campo contiene el identificador de programa (ProgID) de OLE del asistente, o bien una representación de cadena GUID del CLSID del asistente que creó el IDE.|
|Parámetro|Estas partes son opcionales. Puede Agregar tantas como sea necesario.|

Los parámetros permiten que el archivo. vsz pase parámetros personalizados adicionales al asistente. Cada valor se pasa como un elemento de cadena en una matriz de variantes al asistente. Para obtener más información, vea [Custom Parameters](../../extensibility/internals/custom-parameters.md).

Para agregar un ID. de configuración regional predeterminado al archivo. vsz, especifique `FALLBACK_LCID` = XXXX, donde XXXX es el ID. de configuración regional, por ejemplo, 1033 para inglés. Cuando `FALLBACK_LCID` se define el parámetro, el asistente usa el identificador de configuración regional de reserva proporcionado si no se encuentra el identificador actual.

## <a name="see-also"></a>Vea también

- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
