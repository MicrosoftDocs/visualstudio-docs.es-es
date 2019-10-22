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
ms.openlocfilehash: 5726cea8b2e81c53b5f3fff963357946f26b199f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438228"
---
# <a name="how-to-install-a-visualizer"></a>Procedimiento Instalación de un visualizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Instalar un visualizador es un proceso sencillo.  
  
> [!NOTE]
> En **Store** aplicaciones, sólo el texto estándar, se admiten los visualizadores HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).  
  
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
