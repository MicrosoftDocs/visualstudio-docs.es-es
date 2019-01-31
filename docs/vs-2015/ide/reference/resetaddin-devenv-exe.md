---
title: /ResetAddin (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1400e61487a7ad052d5a516019e76149e8e3d31e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755059"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Quita comandos y la interfaz de usuario de comandos asociados al complemento especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argumentos  
 `AddIn`  
 Opcional. El nombre de comando del complemento.  
  
## <a name="remarks"></a>Comentarios  
 De manera predeterminada, el nombre de comando del complemento es igual a *\<AddInSolutionName>*.Connect<em>.\<AddInSolutionName></em>, y aparece en Connect.cs como el parámetro `commandName` del método `Exec`. También puede comprobar el nombre de comando si empieza a escribir el nombre del complemento en la ventana Comandos de Visual Studio y usa Intellisense para rellenar el resto.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente inicia Visual Studio y evita que el complemento `MyAddin` se ejecute en el inicio.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
