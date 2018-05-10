---
title: 'Cómo: Administrar configuraciones de compilación a las que se han aplicado opciones del desarrollador de Visual Basic'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 987419e62d54b44a21a70f625e2a240bd7aecc21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Cómo: Administrar configuraciones de compilación a las que se han aplicado opciones del desarrollador de Visual Basic

De manera predeterminada, todas las opciones de configuración de compilación avanzadas están ocultas con las opciones del desarrollador de Visual Basic aplicadas. En este tema se explica cómo habilitar manualmente estas opciones.

## <a name="enable-advanced-build-configurations"></a>Habilitar las configuraciones de compilación avanzadas

De manera predeterminada, las opciones del desarrollador de Visual Basic ocultan la opción para abrir el cuadro de diálogo **Administrador de configuración** y las listas **Configuración** y **Plataforma** en el [Diseñador de proyectos](..//ide/reference/application-page-project-designer-visual-basic.md).

1.  En el menú **Herramientas** , haga clic en **Opciones**.

2.  Expanda **Proyectos y soluciones** y haga clic en **General**.

    > [!NOTE]
    > El nodo **General** es visible incluso si la opción **Mostrar todas las configuraciones** no está activada. Si quiere ver cada opción disponible, haga clic en **Mostrar todas las configuraciones**.

3.  Haga clic en **Mostrar configuraciones de compilación avanzadas**.

4.  Haga clic en **Aceptar**.

     En el menú **Compilar**, **Administrador de configuración** ahora está disponible y las listas **Configuración** y **Plataforma** están visibles en el **Diseñador de proyectos**.

## <a name="see-also"></a>Vea también

- [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)
- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)