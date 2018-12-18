---
title: 'Cómo: Compilar en un directorio de salida común'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12f45890224684ff2e4c411875ab61bdfb698cfb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942050"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Cómo: Compilar en un directorio de salida común

De manera predeterminada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila cada proyecto en una solución en su propia carpeta dentro de la solución. Puede cambiar las rutas de salida de la compilación de los proyectos para forzar que todos los resultados se almacenen en la misma carpeta.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Para colocar todas las soluciones que se generan en un mismo directorio

1.  Haga clic en un proyecto de la solución.

2.  En el menú **Proyecto**, haga clic en **Propiedades**.

3.  Según el tipo de proyecto, haga clic en la pestaña **Compilar** o en la pestaña **Generar** y establezca la **Ruta de acceso de salida** en una carpeta que se utilizará para todos los proyectos de la solución.

4.  Repita los pasos del 1 al 3 para todos los proyectos de la solución.

## <a name="see-also"></a>Vea también

- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
- [Cómo: Cambiar el directorio de salida de compilación](../ide/how-to-change-the-build-output-directory.md)