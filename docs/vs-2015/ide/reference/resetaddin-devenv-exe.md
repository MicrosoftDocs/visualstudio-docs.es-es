---
title: /ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f306e6952b5cf0d41901b85e554cfc3f444dbb00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567998"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [- /resetaddin (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/resetaddin-devenv-exe).  
  
  
Quita comandos y la interfaz de usuario de comandos asociados al complemento especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argumentos  
 `AddIn`  
 Opcional. El nombre de comando del complemento.  
  
## <a name="remarks"></a>Comentarios  
 De manera predeterminada, el nombre de comando del complemento es igual a *\<AddInSolutionName>*.Connect *.\<AddInSolutionName>*, y aparece en Connect.cs como el parámetro `commandName` del método `Exec`. También puede comprobar el nombre de comando si empieza a escribir el nombre del complemento en la ventana Comandos de Visual Studio y usa Intellisense para rellenar el resto.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente inicia Visual Studio y evita que el complemento `MyAddin` se ejecute en el inicio.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)



