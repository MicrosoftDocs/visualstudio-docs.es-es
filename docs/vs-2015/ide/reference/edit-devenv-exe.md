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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c81f59f2dadf535af4e9a76949a29fd1355c33f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657743"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre el archivo especificado en una instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Sintaxis

```
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Argumentos
 `file1` Opcional. El archivo que se abre en una instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Si no existe ninguna instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], se crea una instancia con un diseño de ventanas simplificado y se abre `file1` en la nueva instancia.

 `file2` Opcional. Uno o más archivos adicionales que se van a abrir en la instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="remarks"></a>Observaciones
 Si no se especifica ningún archivo y ya hay una instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], la instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] recibe el foco. Si no se especifica ningún archivo y no hay ninguna instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], se crea una instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] con un diseño de ventanas simplificado.

 Si la instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] está en un estado modal, por ejemplo, si el cuadro de diálogo [Opciones](../../ide/reference/options-dialog-box-visual-studio.md) está abierto, el archivo se abrirá en la instancia existente cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] salga del estado modal.

## <a name="example"></a>Ejemplo
 En este ejemplo se abre el archivo `MyFile.cs` en una instancia existente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o se abre el archivo en una nueva instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] si todavía no hay ninguna.

```
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Consulte también
 [Modificadores de línea de comandos de devenv](../../ide/reference/devenv-command-line-switches.md)
