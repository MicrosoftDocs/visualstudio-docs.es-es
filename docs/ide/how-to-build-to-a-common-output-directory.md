---
title: 'Cómo: Compilar en un directorio de salida común'
description: Aprenda a cambiar las rutas de salida de compilación de los proyectos para obligar a que todas las salidas se coloquen en la misma carpeta.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a39dae210c2cb9afe3e4b77962b75ddb3be4baeb
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136971"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Cómo: Compilar en un directorio de salida común

De manera predeterminada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila cada proyecto en una solución en su propia carpeta dentro de la solución. Puede cambiar las rutas de salida de la compilación de los proyectos para forzar que todos los resultados se almacenen en la misma carpeta.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Para colocar todas las soluciones que se generan en un mismo directorio

1. Haga clic en un proyecto de la solución.

2. En el menú **Proyecto** , haga clic en **Propiedades** .

3. Según el tipo de proyecto, haga clic en la pestaña **Compilar** o en la pestaña **Generar** y establezca la **Ruta de acceso de salida** en una carpeta que se utilizará para todos los proyectos de la solución.

4. Repita los pasos del 1 al 3 para todos los proyectos de la solución.

## <a name="see-also"></a>Consulta también

- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
- [Procedimiento: Cambio del directorio de salida de compilación](../ide/how-to-change-the-build-output-directory.md)