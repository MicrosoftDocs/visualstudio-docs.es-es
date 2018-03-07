---
title: Modificador InstallVSTemplates devenv.exe| Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 529979caa801ace8dd649cf1614f2eeb27ca070b
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)

El modificador /InstallVSTemplates registra las plantillas de proyecto o elemento incluidas en *\<ruta de instalación de Visual Studio>*\Common7\IDE\ProjectTemplates\ o *\<ruta de instalación de Visual Studio>*\Common7\IDE\ItemTemplates\ para que se pueda obtener acceso a ellas a través de los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento**.

> [!WARNING]
> Este modificador solo se admite para el desarrollo de partners de Visual Studio. Debe ejecutar devenv como administrador para poder usar los modificadores [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) e [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md). Para obtener más información, vea [Permisos del usuario](../../ide/user-permissions-and-visual-studio.md).

## <a name="syntax"></a>Sintaxis

```
devenv.exe /InstallVSTemplates
```

## <a name="see-also"></a>Vea también

[Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)