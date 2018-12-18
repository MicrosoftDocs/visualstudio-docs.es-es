---
title: 'Cómo: instalar un visualizador | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87feaebf16168744467137fdf4af54538a316cdf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473782"
---
# <a name="how-to-install-a-visualizer"></a>Cómo: Instalar un visualizador
Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar un visualizador es un proceso sencillo.  
  
> [!NOTE]
>  En las aplicaciones UWP, sólo el texto estándar, se admiten los visualizadores HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).  
  
### <a name="to-install-a-visualizer"></a>Para instalar un visualizador  
  
1.  Busque el archivo DLL que contiene el visualizador que ha compilado.  
  
2.  Copie el archivo DLL a una de las siguientes ubicaciones:  
  
    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3.  Si desea utilizar un visualizador administrado para la depuración remota, copie el archivo DLL en la misma ruta de acceso en el equipo remoto.  
  
4.  Reinicie la sesión de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Crear los visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: Escribir un visualizador](../debugger/how-to-write-a-visualizer.md)