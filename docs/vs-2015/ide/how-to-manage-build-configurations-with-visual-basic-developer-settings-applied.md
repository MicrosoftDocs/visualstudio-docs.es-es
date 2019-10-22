---
title: 'Cómo: Administrar configuraciones de compilación a las que se han aplicado opciones del desarrollador de Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a5f8568edc636955558ec93b55c0aedebf0065d3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651836"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Cómo: Administrar configuraciones de compilación a las que se han aplicado opciones del desarrollador de Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De manera predeterminada, todas las opciones de configuración de compilación avanzadas están ocultas con las opciones del desarrollador de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] aplicadas. En este tema se explica cómo habilitar manualmente estas opciones.

## <a name="enabling-advanced-build-configurations"></a>Habilitar las configuraciones de compilación avanzadas
 De manera predeterminada, las opciones del desarrollador de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ocultan la opción para abrir el cuadro de diálogo **Administrador de configuración** y las listas **Configuración** y **Plataforma** en el [Diseñador de proyectos](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

#### <a name="to-enable-advanced-build-configurations"></a>Para habilitar las configuraciones de compilación avanzadas

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. Expanda **Proyectos y soluciones** y haga clic en **General**.

    > [!NOTE]
    > El nodo **General** es visible incluso si la opción **Mostrar todas las configuraciones** no está activada. Si quiere ver cada opción disponible, haga clic en **Mostrar todas las configuraciones**.

3. Haga clic en **Mostrar configuraciones de compilación avanzadas**.

4. Haga clic en **Aceptar**.

     En el menú **Compilar**, **Administrador de configuración** ahora está disponible y las listas **Configuración** y **Plataforma** están visibles en el Diseñador de proyectos.

## <a name="see-also"></a>Otras referencias
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md) [compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
