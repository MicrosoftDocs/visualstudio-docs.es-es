---
title: Procedimiento Configuración de proyectos para destinarlos a varias plataformas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4f5a2346a6ae246f9a7676709e35074d71b1437
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028700"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Procedimiento Configuración de proyectos para destinarlos a varias plataformas

Visual Studio proporciona una forma para que una solución tenga como destino varias arquitecturas de CPU diferentes (o plataformas) a la vez. Se tiene acceso a las propiedades que las establecerán a través del cuadro de diálogo **Configuration Manager**.

## <a name="target-a-platform"></a>Elegir una plataforma

El cuadro de diálogo **Configuration Manager** permite crear y establecer plataformas y configuraciones de nivel de proyecto y solución. Cada combinación de destinos y configuraciones de nivel de solución puede tener un conjunto único de propiedades asociadas, lo que le permite cambiar fácilmente entre, por ejemplo, una configuración de lanzamiento que tiene como destino una plataforma [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], una configuración de lanzamiento que tiene como destino una plataforma x86 y una configuración de depuración que tiene como destino una plataforma x86.

1.  En el menú **Compilar**, haga clic en **Configuration Manager**.

2.  En el cuadro **Plataforma de soluciones activas**, seleccione la plataforma que quiere establecer como destino de la solución o seleccione **\<Nuevo>** para crear una plataforma. Visual Studio compilará la aplicación para que tenga como destino la plataforma que se establece como la plataforma activa en el cuadro de diálogo **Configuration Manager**.

## <a name="remove-a-platform"></a>Quitar una plataforma

Si se da cuenta de que no necesita una plataforma, puede quitarla mediante el cuadro de diálogo **Configuration Manager**. Esta acción quitará todas las configuraciones de soluciones y proyectos que haya configurado para esa combinación de configuración y destino.

1.  En el menú **Compilar**, haga clic en **Configuration Manager**.

2.  En el cuadro **Plataforma de soluciones activas**, seleccione **\<Editar>**. Se abre el cuadro de diálogo **Editar plataformas de solución**.

3.  Haga clic en la plataforma que quiera quitar y haga clic en **Quitar**.

## <a name="target-multiple-platforms-with-one-solution"></a>Establecer como destino varias plataformas con una solución

Dado que puede cambiar la configuración en función de la combinación de configuración y plataforma, puede configurar una solución que puede tener como destino más de una plataforma.

### <a name="to-target-multiple-platforms"></a>Para establecer varias plataformas como destino

1.  Use **Configuration Manager** para agregar al menos dos plataformas de destino para la solución.

2.  Seleccione la plataforma que quiera establecer como destino de la lista **Plataforma de soluciones activas**.

3.  Compile la solución.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Para compilar varias configuraciones de solución a la vez

1. Use **Configuration Manager** para agregar al menos dos plataformas de destino para la solución.

2. Use la ventana **Compilación por lotes** para compilar varias configuraciones de solución al mismo tiempo.

   Se puede tener una plataforma de nivel de solución establecida, por ejemplo, en [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] y no tener ningún proyecto dentro de esa solución que tenga como destino la misma plataforma. También se pueden tener varios proyectos en la solución, cada uno de ellos con diferentes plataformas de destino. Se recomienda que, si tiene una de estas situaciones, cree una configuración con un nombre descriptivo para evitar confusiones.

## <a name="see-also"></a>Vea también

- [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)
- [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)
- [Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
