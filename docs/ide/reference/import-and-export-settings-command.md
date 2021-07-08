---
description: Importa, exporta o restablece la configuración de Visual Studio. Extensión de archivo vssettings
title: comando para importar y exportar configuraciones
ms.date: 05/28/2021
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dba50cf598c3c74f6c9407fbef5d55f938941a11
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687643"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Comando Importar y exportar configuraciones (archivo .vssettings)

Importa, exporta o restablece el archivo de configuración de Visual Studio, `.vssettings`.

El esquema del archivo está abierto. Normalmente, el esquema sigue una estructura XML donde cada categoría es una etiqueta que, a su vez, puede contener etiquetas de subcategoría. Estas etiquetas de subcategoría pueden contener etiquetas de valor de propiedad. Aunque en la mayoría de los paquetes se usa la estructura común, cualquier paquete de Visual Studio puede aportar código XML arbitrario al archivo con el esquema que elija.

## <a name="syntax"></a>Sintaxis

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Conmutadores

/export:`filename`

Opcional. Exporta la configuración actual al archivo especificado.

/import:`filename`

Opcional. Importa la configuración al archivo especificado.

/reset

Opcional. Restablece la configuración actual.

## <a name="remarks"></a>Observaciones

Al ejecutar este comando sin modificadores se abre el Asistente **Importar y exportar configuraciones**. Para obtener más información, vea [Sincronizar la configuración](../synchronized-settings-in-visual-studio.md) y [Configuración del entorno](../environment-settings.md).

## <a name="example"></a>Ejemplo

El comando siguiente exporta la configuración actual al archivo `MyFile.vssettings`:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```



## <a name="see-also"></a>Consulte también

- [Configuración del entorno](../../ide/environment-settings.md)
- [Sincronizar la configuración](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
