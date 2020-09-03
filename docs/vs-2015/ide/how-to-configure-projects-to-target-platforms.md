---
title: 'Cómo: Configurar proyectos para plataformas de destino | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6ba899fd1b17fa5a82c64d5c5e44e67f0d5eb97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668189"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Cómo: Configurar proyectos para plataformas de destino
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permite configurar las aplicaciones para distintas plataformas de destino, incluidas las de 64 bits. Para obtener más información sobre la compatibilidad con la plataforma de 64 bits en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , vea [aplicaciones de 64 bits](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).

## <a name="targeting-platforms-with-the-configuration-manager"></a>Configurar plataformas de destino con el Administrador de configuración
 El **Administrador de configuración** proporciona una forma de agregar rápidamente nuevas plataformas de destino para el proyecto. Si selecciona una de las plataformas que se incluyen con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], las propiedades del proyecto se modifican a fin de compilarlo para esa plataforma.

#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Para configurar un proyecto para una plataforma de destino de 64 bits

1. En la barra de menús, elija **Compilar**, **Administrador de configuración**.

2. En la lista **Plataforma de soluciones activas**, elija una plataforma de 64 bits para la solución de destino y luego elija el botón **Cerrar**.

   1. Si la plataforma que desea no aparece en la lista **plataforma de soluciones activas** , elija **nueva**.

        Aparecerá el cuadro de diálogo **Nueva plataforma de solución**.

   2. En la lista **Escriba o seleccione la nueva plataforma**, elija **x64**.

       > [!NOTE]
       > Si asigna un nuevo nombre a la configuración, es posible que tenga que modificar la configuración del **Diseñador de proyectos** para seleccionar la plataforma correcta como destino.

   3. Si quiere copiar la configuración de una configuración de plataforma actual, selecciónela y luego elija el botón **Aceptar**.

   Se actualizarán las propiedades de todos los proyectos que tienen como destino la plataforma de 64 bits y la próxima compilación del proyecto se optimizará para plataformas de 64 bits.

## <a name="targeting-platforms-in-the-project-designer"></a>Configurar plataformas de destino en el Diseñador de proyectos
 El Diseñador de proyectos también proporciona una forma de configurar distintas plataformas para el proyecto de destino. Si la selección de una de las plataformas incluidas en la lista del cuadro de diálogo **Nueva plataforma de solución** no funciona para la solución, puede crear un nombre de configuración personalizado y modificar la configuración en el **Diseñador de proyectos** a fin de configurar el proyecto para la plataforma de destino apropiada.

 La realización de esta tarea varía según el lenguaje de programación utilizado. Para obtener más información, vea los siguientes vínculos:

- Para proyectos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], vea [/platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

- Para los [!INCLUDE[csprcs](../includes/csprcs-md.md)] proyectos de, vea [compilar (página, diseñador de proyectos) (C#)](../ide/reference/build-page-project-designer-csharp.md).

- Para los [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] proyectos de, vea [/CLR (Common Language Runtime Compilation)](https://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).

## <a name="see-also"></a>Consulte también
 [Descripción de las plataformas de compilación](../ide/understanding-build-platforms.md) [/Platform (opciones del compilador de C#)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04) [64 de aplicaciones de bits de](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181) [Visual Studio IDE 64](../ide/visual-studio-ide-64-bit-support.md) bits
