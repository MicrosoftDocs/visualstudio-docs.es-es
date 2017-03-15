---
title: "Importar y exportar configuraci&#243;n (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Tools.ImportandExportSettings"
helpviewer_keywords: 
  - "Tools.ImportandExportSettings"
  - "comando para importar y exportar configuraciones"
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Importar y exportar configuraci&#243;n (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Importa, exporta o restablece la configuración de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintaxis  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## Modificadores  
 \/export:`filename`  
 Opcional.  Exporta la configuración actual al archivo especificado.  
  
 \/import:`filename`  
 Opcional.  Importa la configuración en el archivo especificado.  
  
 \/reset  
 Opcional.  Restablece la configuración actual.  
  
## Comentarios  
 Al ejecutar este comando sin modificadores, se abre el **Asistente para importar y exportar configuraciones**.  Para obtener más información, vea [How to: Share Settings Between Computers or Visual Studio Versions](http://msdn.microsoft.com/es-es/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## Ejemplo  
 El comando siguiente exporta la actual configuración al archivo `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## Vea también  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)