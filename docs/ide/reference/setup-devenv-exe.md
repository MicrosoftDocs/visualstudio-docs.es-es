---
title: Conmutador /setup devenv.exe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f03de74540d130d66ce123b355691e0828b93e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

El conmutador /Setup provoca que Visual Studio combine los metadatos de recursos que describen menús, barras de herramientas y grupos de comandos de todos los VSPackages disponibles.

## <a name="syntax"></a>Sintaxis

```
devenv /setup
```

## <a name="remarks"></a>Comentarios

Este modificador no toma ningún argumento. El comando `devenv /setup` suele ser el último paso del proceso de instalación. El uso del conmutador `/setup` no inicia Visual Studio.

Debe ejecutar `devenv` como administrador para poder usar los modificadores [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) y [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) .

## <a name="example"></a>Ejemplo

En este ejemplo se muestra el último paso de la instalación de una versión de Visual Studio que incluye VSPackages.

```
devenv /setup
```

## <a name="see-also"></a>Vea también

[Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)