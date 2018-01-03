---
title: Comando Abrir proyecto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6ae2b8f0c9f0a17f29bf42a8a2893f8671df4cd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="open-project-command"></a>Abrir proyecto (Comando)
Abre un proyecto existente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Argumentos  
 `filename`  
 Obligatorio. Ruta de acceso completa y nombre de archivo del proyecto que se va a abrir.  
  
 La sintaxis del argumento `filename` requiere que las rutas de acceso que contienen espacios se incluyan entre comillas.  
  
## <a name="remarks"></a>Comentarios  
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.  
  
 Este comando no está disponible durante la depuración.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se abre el proyecto Test1 de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)].  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)