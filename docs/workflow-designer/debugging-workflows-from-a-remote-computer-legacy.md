---
title: Depurar flujos de trabajo desde un equipo remoto (heredado) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: e6a3058d61d2aff0369fd52e1f03726a91a2267c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Depurar flujos de trabajo desde un equipo remoto (Heredado)
Este tema describe cómo depurar heredadas remotas [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] las aplicaciones que se generan con el Diseñador de flujo de trabajo de Windows heredado. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando la aplicación deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Al instalar [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], una de las opciones de instalación de componentes es instalar el [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] del depurador para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. De esta forma se instalan los componentes de depuración remota. Estos componentes de depuración remota se deben instalar en el equipo de destino de la depuración del flujo de trabajo remota.

 Además, el ensamblado que contiene la definición de flujo de trabajo del flujo de trabajo heredado que está depurando en un equipo remoto debe estar instalado en la caché global de ensamblados (GAC) del equipo local desde el que se realiza la depuración. Por ejemplo, si un flujo de trabajo heredado se está ejecutando en el equipo remoto A y está depurándolo desde el equipo local B, la definición de flujo de trabajo debe encontrarse en la GAC del equipo B. De esta forma, el diseñador puede deserializar y mostrar en el equipo B el marcado del flujo de trabajo que se está ejecutando de forma remota en el equipo A. Para obtener más información sobre la caché global de ensamblados, vea MSDN Library.

 La depuración remota de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] funciona de la misma forma que la depuración remota de otros componentes de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] la depuración remota en MSDN Library.

## <a name="see-also"></a>Vea también

- [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)