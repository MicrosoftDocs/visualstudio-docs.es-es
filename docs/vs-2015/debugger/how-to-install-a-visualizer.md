---
title: Procedimiento Instalar un visualizador | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 2e223831b30f784094a2affa5cebb314cc6e997f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059713"
---
# <a name="how-to-install-a-visualizer"></a>Procedimiento Instalación de un visualizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Instalar un visualizador es un proceso sencillo.  
  
> [!NOTE]
>  En **Store** aplicaciones, sólo el texto estándar, se admiten los visualizadores HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).  
  
### <a name="to-install-a-visualizer"></a>Para instalar un visualizador  
  
1. Busque el archivo DLL que contiene el visualizador que ha compilado.  
  
2. Copie el archivo DLL a una de las siguientes ubicaciones:  
  
    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3. Si desea utilizar un visualizador administrado para la depuración remota, copie el archivo DLL en la misma ruta de acceso en el equipo remoto.  
  
4. Reinicie la sesión de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Creación de visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: Escritura de un visualizador](../debugger/how-to-write-a-visualizer.md)
