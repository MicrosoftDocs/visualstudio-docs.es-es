---
title: Comando para importar y exportar configuraciones | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4a638686bb0ec111bf551cac0b38bb5d50b1774
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573953"
---
# <a name="import-and-export-settings-command"></a>comando para importar y exportar configuraciones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [importar y exportar configuración de comando](https://docs.microsoft.com/visualstudio/ide/reference/import-and-export-settings-command).  
  
  
Importa, exporta o restablece la configuración de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
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
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)



