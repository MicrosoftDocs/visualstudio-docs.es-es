---
title: 'Cómo: Configurar proyectos para múltiples plataformas de destino | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bb759faff99b641f24df87f73bc1d3d52b6635cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663559"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Cómo: Configurar proyectos para múltiples plataformas de destino
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona una forma para que una solución tenga como destino varias arquitecturas de CPU diferentes (o plataformas) a la vez. Se tiene acceso a las propiedades que las establecerán a través del cuadro de diálogo **Configuration Manager**.

## <a name="targeting-a-platform"></a>Elegir una plataforma como destino
 El cuadro de diálogo **Configuration Manager** permite crear y establecer plataformas y configuraciones de nivel de proyecto y solución. Cada combinación de destinos y configuraciones de nivel de solución puede tener un conjunto único de propiedades asociadas, lo que le permite cambiar fácilmente entre, por ejemplo, una configuración de lanzamiento que tiene como destino una plataforma [!INCLUDE[vcprx64](../includes/vcprx64-md.md)], una configuración de lanzamiento que tiene como destino una plataforma x86 y una configuración de depuración que tiene como destino una plataforma x86.

#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Para establecer la configuración para que tenga como destino otra plataforma

1. En el menú **Compilar**, haga clic en **Configuration Manager**.

2. En el cuadro **Plataforma de soluciones activas**, seleccione la plataforma que quiere establecer como destino de la solución o seleccione **\<New>** para crear una plataforma. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compilará la aplicación para que tenga como destino la plataforma que se establece como la plataforma activa en el cuadro de diálogo **Configuration Manager**.

## <a name="removing-a-platform"></a>Quitar una plataforma
 Si se da cuenta de que no necesita una plataforma, puede quitarla mediante el cuadro de diálogo Configuration Manager. Esta acción quitará todas las configuraciones de soluciones y proyectos que haya configurado para esa combinación de configuración y destino.

#### <a name="to-remove-a-platform"></a>Para quitar una plataforma

1. En el menú **Compilar**, haga clic en **Configuration Manager**.

2. En el cuadro **Plataforma de soluciones activas**, seleccione **\<Edit>** . Se abre el cuadro de diálogo **Editar plataformas de solución**.

3. Haga clic en la plataforma que quiera quitar y haga clic en **Quitar**.

## <a name="targeting-multiple-platforms-with-one-solution"></a>Establecer como destino varias plataformas con una solución
 Dado que puede cambiar la configuración en función de la combinación de configuración y plataforma, puede configurar una solución que puede tener como destino más de una plataforma.

#### <a name="to-target-multiple-platforms"></a>Para establecer varias plataformas como destino

1. Use **Configuration Manager** para agregar al menos dos plataformas de destino para la solución.

2. Seleccione la plataforma que quiera establecer como destino de la lista **Plataforma de soluciones activas**.

3. Compile la solución.

#### <a name="to-build-multiple-solution-configurations-at-once"></a>Para compilar varias configuraciones de solución a la vez

1. Use **Configuration Manager** para agregar al menos dos plataformas de destino para la solución.

2. Use la ventana **Compilación por lotes** para compilar varias configuraciones de solución al mismo tiempo.

   Se puede tener una plataforma de nivel de solución establecida, por ejemplo, en [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] y no tener ningún proyecto dentro de esa solución que tenga como destino la misma plataforma. También se pueden tener varios proyectos en la solución, cada uno de ellos con diferentes plataformas de destino. Se recomienda que, si tiene una de estas situaciones, cree una configuración con un nombre descriptivo para evitar confusiones.

## <a name="see-also"></a>Consulte también
 [Cómo: crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md) [Descripción](../ide/understanding-build-configurations.md) [de las configuraciones de compilación compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
