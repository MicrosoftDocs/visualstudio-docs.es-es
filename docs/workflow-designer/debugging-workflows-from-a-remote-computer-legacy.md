---
title: "Depurar flujos de trabajo desde un equipo remoto (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "depurar flujos de trabajo, remotamente"
  - "depurar, remoto"
  - "depuración remota, flujos de trabajo"
  - "flujos de trabajo, depuración remota"
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Depurar flujos de trabajo desde un equipo remoto (Heredado)
En este tema se describe cómo depurar aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] heredadas remotas compiladas con [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado.Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando la aplicación deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Cuando instala [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], una de las opciones de instalación de componentes es instalar el Depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)].De esta forma, se instalan los componentes de depuración remota.Estos componentes de depuración remota se deben instalar en el equipo de destino de la depuración del flujo de trabajo remota.  
  
 Además, el ensamblado que contiene la definición de flujo de trabajo del flujo de trabajo heredado que está depurando en un equipo remoto debe estar instalado en la caché global de ensamblados \(GAC\) del equipo local desde el que se realiza la depuración.Por ejemplo, si un flujo de trabajo heredado se está ejecutando en un equipo remoto A y lo está depurando desde el equipo local B, la definición de flujo de trabajo debe estar presente en la GAC del equipo B.Esto permite al diseñador deserializar y mostrar en el equipo B el marcado del flujo de trabajo que se está ejecutando de forma remota en el equipo A.Para obtener más información sobre la caché global de ensamblados, vea MSDN Library.  
  
 La depuración remota de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] funciona de la misma forma que la depuración remota de otros componentes de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].Para obtener más información, vea la depuración remota de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] en la biblioteca de MSDN.  
  
## Vea también  
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)