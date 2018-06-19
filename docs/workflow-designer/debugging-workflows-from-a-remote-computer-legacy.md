---
title: Diseñador de flujo de trabajo - depurar flujos de trabajo desde un equipo remoto (heredado)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 391180cd76fe5e0cccca802ba1cbfb78277dabc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31967913"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Depurar flujos de trabajo desde un equipo remoto (Heredado)

En este tema se describe cómo depurar remoto aplicaciones heredadas de Windows Workflow Foundation (WF) que se generan con el Diseñador de flujo de trabajo de Windows heredado. Use el Diseñador de flujo de trabajo heredado cuando la aplicación deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

 Cuando se instala Visual Studio, una de las opciones de instalación de componentes es instalar el Visual Studio depurador de Windows Workflow Foundation (WF). De esta forma se instalan los componentes de depuración remota. Estos componentes de depuración remota se deben instalar en el equipo de destino de la depuración del flujo de trabajo remota.

 Además, el ensamblado que contiene la definición de flujo de trabajo del flujo de trabajo heredado que está depurando en un equipo remoto debe estar instalado en la caché global de ensamblados (GAC) del equipo local desde el que se realiza la depuración. Por ejemplo, si un flujo de trabajo heredado se está ejecutando en el equipo remoto A y está depurándolo desde el equipo local B, la definición de flujo de trabajo debe encontrarse en la GAC del equipo B. De esta forma, el diseñador puede deserializar y mostrar en el equipo B el marcado del flujo de trabajo que se está ejecutando de forma remota en el equipo A. Para obtener más información sobre la caché global de ensamblados, vea MSDN Library.

 La depuración remota de Windows Workflow Foundation funciona igual que la depuración remota de otros componentes de Visual Studio. Para obtener más información, vea Visual Studio depuración remota en MSDN Library.

## <a name="see-also"></a>Vea también

- [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)