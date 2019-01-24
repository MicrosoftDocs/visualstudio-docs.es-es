---
title: 'Cómo: instalar un visualizador | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5b2c77bd5f9d32b3bb4a0954017b7abdee1947c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731468"
---
# <a name="how-to-install-a-visualizer"></a>Cómo: Instalar un visualizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Instalar un visualizador es un proceso sencillo.  
  
> [!NOTE]
>  En **Store** aplicaciones, sólo el texto estándar, se admiten los visualizadores HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).  
  
### <a name="to-install-a-visualizer"></a>Para instalar un visualizador  
  
1.  Busque el archivo DLL que contiene el visualizador que ha compilado.  
  
2.  Copie el archivo DLL a una de las siguientes ubicaciones:  
  
    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3.  Si desea utilizar un visualizador administrado para la depuración remota, copie el archivo DLL en la misma ruta de acceso en el equipo remoto.  
  
4.  Reinicie la sesión de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Crear visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: Escribir un visualizador](../debugger/how-to-write-a-visualizer.md)



