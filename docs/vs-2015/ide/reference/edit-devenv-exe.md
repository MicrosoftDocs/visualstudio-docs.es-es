---
title: -Edit (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b25e7bb0f6498e9160dd8602648ced28b3bb9fed
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780519"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Abre el archivo especificado en una instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Argumentos  
 `file1`  
 Opcional. El archivo que se abre en una instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Si no existe ninguna instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], se crea una instancia con un diseño de ventanas simplificado y se abre `file1` en la nueva instancia.  
  
 `file2`  
 Opcional. Uno o más archivos adicionales que se van a abrir en la instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="remarks"></a>Comentarios  
 Si no se especifica ningún archivo y ya hay una instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], la instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] recibe el foco. Si no se especifica ningún archivo y no hay ninguna instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], se crea una instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] con un diseño de ventanas simplificado.  
  
 Si la instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] está en un estado modal, por ejemplo, si el cuadro de diálogo [Opciones](../../ide/reference/options-dialog-box-visual-studio.md) está abierto, el archivo se abrirá en la instancia existente cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] salga del estado modal.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se abre el archivo `MyFile.cs` en una instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o se abre el archivo en una nueva instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] si todavía no hay ninguna.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
