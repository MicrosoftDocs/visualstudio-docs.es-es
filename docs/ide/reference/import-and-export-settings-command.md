---
title: comando para importar y exportar configuraciones
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f212e5c5becb8cf2ae575510825a9c7c9034222
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388713"
---
# <a name="import-and-export-settings-command"></a>comando para importar y exportar configuraciones

Importa, exporta o restablece la configuración de Visual Studio.

## <a name="syntax"></a>Sintaxis

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Modificadores

/export:`filename`

Opcional. Exporta la configuración actual al archivo especificado.

/import:`filename`

Opcional. Importa la configuración al archivo especificado.

/reset

Opcional. Restablece la configuración actual.

## <a name="remarks"></a>Comentarios

Al ejecutar este comando sin modificadores se abre el Asistente **Importar y exportar configuraciones**. Para obtener más información, vea [Sincronizar la configuración](../synchronized-settings-in-visual-studio.md) y [Configuración del entorno](../environment-settings.md).

## <a name="example"></a>Ejemplo

El comando siguiente exporta la configuración actual al archivo `MyFile.vssettings`:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Vea también

- [Configuración del entorno](../../ide/environment-settings.md)
- [Sincronizar la configuración](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)