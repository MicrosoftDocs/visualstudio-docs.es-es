---
title: "Cómo: Compilar en un directorio de resultados común | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0082f69e0c35bb84a15a8dd4798e7a17b6a3dd7c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-build-to-a-common-output-directory"></a>Cómo: Compilar en un directorio de resultados común
De manera predeterminada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila cada proyecto en una solución en su propia carpeta dentro de la solución. Puede cambiar las rutas de salida de la compilación de los proyectos para forzar que todos los resultados se almacenen en la misma carpeta.  
  
### <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Para colocar todas las soluciones que se generan en un mismo directorio  
  
1.  Haga clic en un proyecto de la solución.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades**.  
  
3.  Según el tipo de proyecto, haga clic en la pestaña **Compilar** o en la pestaña **Generar** y establezca la **Ruta de acceso de salida** en una carpeta que se utilizará para todos los proyectos de la solución.  
  
4.  Repita los pasos del 1 al 3 para todos los proyectos de la solución.  
  
## <a name="see-also"></a>Vea también  
 [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)   
 [Cómo: Cambiar el directorio de resultados de compilación](../ide/how-to-change-the-build-output-directory.md)