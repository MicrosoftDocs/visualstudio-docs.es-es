---
title: Depurar flujos de trabajo desde un equipo remoto (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bce98714832042471145bcf7d908a62b15bdb144
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656856"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Depurar flujos de trabajo desde un equipo remoto (Heredado)
En este tema se describe cómo depurar aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] heredadas remotas compiladas con [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando la aplicación deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Al instalar [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)], una de las opciones de instalación de componentes consiste en instalar el depurador de [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] para [!INCLUDE[wf](../includes/wf-md.md)]. De esta forma se instalan los componentes de depuración remota. Estos componentes de depuración remota se deben instalar en el equipo de destino de la depuración del flujo de trabajo remota.

 Además, el ensamblado que contiene la definición de flujo de trabajo del flujo de trabajo heredado que está depurando en un equipo remoto debe estar instalado en la caché global de ensamblados (GAC) del equipo local desde el que se realiza la depuración. Por ejemplo, si un flujo de trabajo heredado se está ejecutando en el equipo remoto A y está depurándolo desde el equipo local B, la definición de flujo de trabajo debe encontrarse en la GAC del equipo B. De esta forma, el diseñador puede deserializar y mostrar en el equipo B el marcado del flujo de trabajo que se está ejecutando de forma remota en el equipo A. Para obtener más información sobre la caché global de ensamblados, vea MSDN Library.

 La depuración remota de [!INCLUDE[wf2](../includes/wf2-md.md)] funciona de la misma forma que la depuración remota de otros componentes de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información, vea [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] depuración remota en MSDN Library.

## <a name="see-also"></a>Vea también
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)