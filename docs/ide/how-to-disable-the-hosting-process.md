---
title: 'Cómo: Deshabilitar el proceso de hospedaje'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7970ff97c7aec42f8798da07cf2a4a2b6c8bea8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942066"
---
# <a name="how-to-disable-the-hosting-process"></a>Cómo: Deshabilitar el proceso de hospedaje

Las llamadas a ciertas API pueden verse afectadas cuando se habilita el proceso de hospedaje. En estos casos, es necesario deshabilitar el proceso de hospedaje para devolver los resultados correctos.

## <a name="to-disable-the-hosting-process"></a>Para deshabilitar el proceso de hospedaje

1.  Abra un proyecto ejecutable en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Los proyectos que no generan archivos ejecutables (por ejemplo, proyectos de biblioteca de clases o de servicio) no tienen esta opción.

2.  En el menú **Proyecto**, haga clic en **Propiedades**.

3.  Haga clic en la pestaña **Depurar**.

4.  Desactive la casilla **Habilitar el proceso de hospedaje de Visual Studio**.

 Cuando se deshabilita el proceso de hospedaje, varias características de depuración no están disponibles o sufren una disminución de rendimiento. Para obtener más información, consulte [Debug and the hosting process](../debugger/debugging-and-the-hosting-process.md) (Depuración y proceso de hospedaje).

 En general, cuando se deshabilita el proceso de hospedaje:

-   Aumenta el tiempo necesario para empezar a depurar las aplicaciones de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

-   No está disponible la evaluación de expresiones en tiempo de diseño.

-   No está disponible la depuración de confianza parcial.

## <a name="see-also"></a>Vea también

- [Depuración y proceso de hospedaje](../debugger/debugging-and-the-hosting-process.md)
- [Proceso de hospedaje (vshost.exe)](../ide/hosting-process-vshost-exe.md)