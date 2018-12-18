---
title: Comando Abrir proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: b25ee0e6ba4dfa5c29d5a009087afb55509d0c08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263927"
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
 Requerido. Ruta de acceso completa y nombre de archivo del proyecto que se va a abrir.  
  
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



