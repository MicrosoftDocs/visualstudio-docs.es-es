---
title: Comando para importar y exportar configuraciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: ad7da7f8d83cd45e7cc7801d430dbf70887747b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="import-and-export-settings-command"></a>comando para importar y exportar configuraciones
Importa, exporta o restablece la configuración de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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

Al ejecutar este comando sin modificadores se abre el Asistente **Importar y exportar configuraciones**. Para obtener más información, vea [Configuración sincronizada en Visual Studio](../../ide/synchronized-settings-in-visual-studio.md).

## <a name="example"></a>Ejemplo

El comando siguiente exporta la configuración actual al archivo `MyFile.vssettings`.

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Vea también

[Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)  
[Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)