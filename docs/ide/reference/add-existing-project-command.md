---
title: Comando Agregar proyecto existente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 61f9735c61538465088b58f25e6c714a2441e34c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="add-existing-project-command"></a>Agregar proyecto existente (Comando)
Agrega un proyecto existente a la solución actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Argumentos  
 `filename`  
 Opcional. El nombre del proyecto y la ruta de acceso completa, con extensión, del proyecto que se agregará a la solución.  
  
 Si el argumento `filename` incluye espacios, debe incluirse entre comillas.  
  
 Si no se especifica ningún nombre de archivo, el comando abrirá el cuadro de diálogo de archivo para que el usuario pueda elegir un proyecto.  
  
## <a name="remarks"></a>Comentarios  
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se agrega el proyecto TestProject1 de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] a la solución actual.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)