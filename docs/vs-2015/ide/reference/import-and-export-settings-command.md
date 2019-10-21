---
title: Comando para importar y exportar configuraciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e3ee8549fd8cf1a4551818c013551ba24128f95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671054"
---
# <a name="import-and-export-settings-command"></a>comando para importar y exportar configuraciones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Importa, exporta o restablece la configuración de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Sintaxis

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Modificadores
 /export:`filename` opcional. Exporta la configuración actual al archivo especificado.

 /Import: `filename` opcional. Importa la configuración al archivo especificado.

 /reset Opcional. Restablece la configuración actual.

## <a name="remarks"></a>Comentarios
 Al ejecutar este comando sin modificadores se abre el Asistente **Importar y exportar configuraciones**. Para obtener más información, vea [Cómo: Compartir valores de configuración entre equipos o versiones de Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).

## <a name="example"></a>Ejemplo
 El comando siguiente exporta la configuración actual al archivo `MyFile.vssettings`.

```
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Otras referencias
 [Personalizar la configuración de desarrollo en Visual Studio comandos de](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Visual](../../ide/reference/visual-studio-commands.md) Studio
