---
title: Procedimiento Instalar un visualizador | Documentos de Microsoft
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9b09bc837cae4eaad2c0dbcb2bb82a7daa248eb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63389319"
---
# <a name="how-to-install-a-visualizer"></a>Procedimiento Instalación de un visualizador
Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar un visualizador es un proceso sencillo.

> [!NOTE]
> En aplicaciones UWP, sólo el texto estándar, se admiten los visualizadores HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).

### <a name="to-install-a-visualizer"></a>Para instalar un visualizador

1. Busque el archivo DLL que contiene el visualizador que ha compilado.

2. Copie el archivo DLL a una de las siguientes ubicaciones:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Si desea utilizar un visualizador administrado para la depuración remota, copie el archivo DLL en la misma ruta de acceso en el equipo remoto.

4. Reinicie la sesión de depuración.

## <a name="see-also"></a>Vea también
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
- [Cómo: Escritura de un visualizador](/visualstudio/debugger/create-custom-visualizers-of-data)