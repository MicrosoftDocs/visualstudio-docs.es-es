---
title: Comando para importar y exportar configuraciones | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61924f7d9430661114f1fecc36d585e2d223604b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
 Al ejecutar este comando sin modificadores se abre el Asistente **Importar y exportar configuraciones**. Para obtener más información, vea [Cómo: Compartir valores de configuración entre equipos o versiones de Visual Studio](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Ejemplo  
 El comando siguiente exporta la configuración actual al archivo `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)