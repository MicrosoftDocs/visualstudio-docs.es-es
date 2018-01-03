---
title: -Edit (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 34b256a788f2ce8077d7f62921a63565f210139a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Abre el archivo especificado en una instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Argumentos  
 `file1`  
 Opcional. El archivo que se abre en una instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Si no existe ninguna instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se crea una instancia con un diseño de ventanas simplificado y se abre `file1` en la nueva instancia.  
  
 `file2`  
 Opcional. Uno o más archivos adicionales que se van a abrir en la instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="remarks"></a>Comentarios  
 Si no se especifica ningún archivo y ya hay una instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], la instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recibe el foco. Si no se especifica ningún archivo y no hay ninguna instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se crea una instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con un diseño de ventanas simplificado.  
  
 Si la instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está en un estado modal, por ejemplo, si el cuadro de diálogo [Opciones](../../ide/reference/options-dialog-box-visual-studio.md) está abierto, el archivo se abrirá en la instancia existente cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] salga del estado modal.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se abre el archivo `MyFile.cs` en una instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o se abre el archivo en una nueva instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si todavía no hay ninguna.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)