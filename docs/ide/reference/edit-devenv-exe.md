---
title: -Edit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22c5aeffae35a4202577cf8065b76b1968616355
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Abre el archivo especificado en una instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sintaxis

```cmd
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

```cmd
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)