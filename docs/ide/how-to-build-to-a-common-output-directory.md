---
title: Procedimiento Compilación en un directorio de salida común
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea36368a60fc08d6a818d1ca1e66cfb92d814478
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030774"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Procedimiento Compilación en un directorio de salida común

De manera predeterminada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila cada proyecto en una solución en su propia carpeta dentro de la solución. Puede cambiar las rutas de salida de la compilación de los proyectos para forzar que todos los resultados se almacenen en la misma carpeta.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Para colocar todas las soluciones que se generan en un mismo directorio

1.  Haga clic en un proyecto de la solución.

2.  En el menú **Proyecto**, haga clic en **Propiedades**.

3.  Según el tipo de proyecto, haga clic en la pestaña **Compilar** o en la pestaña **Generar** y establezca la **Ruta de acceso de salida** en una carpeta que se utilizará para todos los proyectos de la solución.

4.  Repita los pasos del 1 al 3 para todos los proyectos de la solución.

## <a name="see-also"></a>Vea también

- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
- [Cómo: Cambio del directorio de salida de compilación](../ide/how-to-change-the-build-output-directory.md)