---
title: 'Cómo: Compilar en un directorio de resultados común | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f85ff51b93383d2deca409a00a3db130d52b5003
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645412"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Cómo: Compilar en un directorio de resultados común
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De manera predeterminada, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compila cada proyecto en una solución en su propia carpeta dentro de la solución. Puede cambiar las rutas de salida de la compilación de los proyectos para forzar que todos los resultados se almacenen en la misma carpeta.

### <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Para colocar todas las soluciones que se generan en un mismo directorio

1. Haga clic en un proyecto de la solución.

2. En el menú **Proyecto**, haga clic en **Propiedades**.

3. Según el tipo de proyecto, haga clic en la pestaña **Compilar** o en la pestaña **Generar** y establezca la **Ruta de acceso de salida** en una carpeta que se utilizará para todos los proyectos de la solución.

4. Repita los pasos del 1 al 3 para todos los proyectos de la solución.

## <a name="see-also"></a>Vea también
 [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md) [Cómo: cambiar el directorio de salida de la compilación](../ide/how-to-change-the-build-output-directory.md)
