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
ms.openlocfilehash: 241d97dd7b2b939ff49656e2cef2c93e4cb9b57b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656051"
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
