---
title: Comando Agregar proyecto existente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7523db6598a32c76944c22bfdabe56ee288c6b43
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54771087"
---
# <a name="add-existing-project-command"></a>Agregar proyecto existente (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 En este ejemplo, se agrega el proyecto TestProject1 de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] a la solución actual.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
