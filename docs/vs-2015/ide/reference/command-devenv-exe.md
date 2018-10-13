---
title: -Command (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5f95d8758da77f1b720f0a1b6ca74f7ac753d805
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254393"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Ejecuta el comando especificado después de iniciar el entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Argumentos  
 `CommandName`  
 Requerido. Nombre completo de un comando de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o su alias, incluido entre comillas dobles. Para obtener más información sobre la sintaxis de comandos y de alias, consulte [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Comentarios  
 Una vez completado el inicio, el IDE ejecuta el comando indicado. Si se usa este modificador, el IDE no muestra la página principal de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] al iniciarse.  
  
 Si un complemento muestra un comando, puede utilizar este modificador para iniciar el complemento desde la línea de comandos. Para obtener más información, consulte [Cómo: Controlar complementos con el Administrador de complementos](http://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y ejecuta automáticamente la macro Open Favorite Files.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



