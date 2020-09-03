---
title: -InstallVSTemplates (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
ms.assetid: 1fb466f6-7955-4535-a840-d93eb8aaa492
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2f019af21beba231a5f135c49fb00dcb463e110
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671016"
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Registra las plantillas de proyecto o elemento que se encuentran en *\<Visual Studio installation path>* \Common7\IDE\ProjectTemplates\ o *\<Visual Studio installation path>* \Common7\IDE\ItemTemplates\ para que se pueda obtener acceso a ellas a través de los cuadros de diálogo **nuevo proyecto** y **Agregar nuevo elemento** .

> [!WARNING]
> Este modificador solo se admite para el desarrollo de partners de Visual Studio, y no está disponible en las ediciones Express. Debe ejecutar devenv como administrador para poder usar los modificadores [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) e [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md). Para obtener más información, vea [Permisos del usuario](../../ide/user-permissions-and-visual-studio.md).

## <a name="syntax"></a>Sintaxis

```
devenv.exe /InstallVSTemplates
```

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también
 [Modificadores de línea de comandos de devenv](../../ide/reference/devenv-command-line-switches.md)
