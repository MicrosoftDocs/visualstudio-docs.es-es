---
title: "Cómo: Especificar qué destino utilizar primero al compilar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a9004bb5335cb06656e378485460ea87093e4372
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-specify-which-target-to-build-first"></a>Cómo: Especificar qué destino utilizar primero al compilar
Un archivo del proyecto puede contener uno o vario elementos `Target` que definen cómo se compila el proyecto. El motor [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) compila el primer proyecto que encuentra, así como las dependencias, a menos que el archivo del proyecto contenga un atributo `DefaultTargets`, un atributo `InitialTargets` o que un destino se especifique en la línea de comandos mediante el modificador **/target**.  
  
## <a name="using-the-initialtargets-attribute"></a>Usar el atributo InitialTargets  
 El atributo `InitialTargets` del elemento `Project` especifica un destino que se ejecutará en primer lugar, incluso si los destinos se especifican en la línea de comandos o en el atributo `DefaultTargets`.  
  
#### <a name="to-specify-one-initial-target"></a>Para especificar un destino inicial  
  
-   Especifique el destino predeterminado en el atributo `InitialTargets` del elemento `Project`. Por ejemplo:  
  
     `<Project InitialTargets="Clean">`  
  
 Puede especificar más de un destino inicial en el atributo `InitialTargets` enumerando los destinos en orden y utilizando un punto y coma para separar cada destino. Los objetivos de la lista se ejecutarán secuencialmente.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Para especificar más de un destino inicial  
  
-   Enumere los destinos iniciales, separados por punto y coma, en el atributo `InitialTargets` del elemento `Project`. Por ejemplo, para ejecutar el destino `Clean` y, a continuación, el destino `Compile`, escriba:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Usar el atributo DefaultTargets  
 El atributo `DefaultTargets` del elemento `Project` especifica qué destinos se compilan si un destino no se especifica explícitamente en la línea de comandos. Si se especifican los destinos en los atributos `InitialTargets` y `DefaultTargets` y no se especifica ningún destino en la línea de comandos, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ejecuta los destinos especificados en el atributo `InitialTargets` seguido por los destinos especificados en el atributo `DefaultTargets`.  
  
#### <a name="to-specify-one-default-target"></a>Para especificar un destino predeterminado  
  
-   Especifique el destino predeterminado en el atributo `DefaultTargets` del elemento `Project`. Por ejemplo:  
  
     `<Project DefaultTargets="Compile">`  
  
 Puede especificar más de un destino predeterminado en el atributo `DefaultTargets` enumerando los destinos en orden y utilizando un punto y coma para separar cada destino. Los objetivos de la lista se ejecutarán secuencialmente.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Para especificar más de un destino predeterminado  
  
-   Enumere los destinos predeterminados, separados por punto y coma, en el atributo `DefaultTargets` del elemento `Project`. Por ejemplo, para ejecutar el destino `Clean` y, a continuación, el destino `Compile`, escriba:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Usar el modificador /target  
 Si un destino predeterminado no está definido en el archivo del proyecto, o si no quiere utilizar ese destino predeterminado, puede utilizar el modificador de línea de comandos **/target** para especificar un destino diferente. Los destinos especificados con el modificador **/target** se ejecutan en lugar de los destinos especificados por el atributo `DefaultTargets`. Los destinos especificados en el atributo `InitialTargets` siempre se ejecutan primero.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Para utilizar primero un destino distinto del destino predeterminado  
  
-   Especifique el destino como el primer destino mediante el modificador de línea de comandos **/target**. Por ejemplo:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Para utilizar primero varios destinos distintos de los destinos predeterminados  
  
-   Enumere los destinos, separados por punto y coma o comas, mediante el conmutador de línea de comandos **/target**. Por ejemplo:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Vea también
  [MSBuild](../msbuild/msbuild.md)  
 [Destinos](../msbuild/msbuild-targets.md)   
 [Cómo: Limpiar una compilación](../msbuild/how-to-clean-a-build.md)