---
title: Comando Abrir proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e2e945eb2faa492f576a0fd0a15fc0bd0e9b208e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652428"
---
# <a name="open-project-command"></a>Abrir proyecto (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 En este ejemplo, se abre el proyecto Test1 de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
