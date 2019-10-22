---
title: Procedimiento Instalación de ensamblados de interoperabilidad primarios de Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee6755a2d795d2018136785986a5a346ddc07dc6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551796"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Procedimiento Instalación de ensamblados de interoperabilidad primarios de Office
  Instale los ensamblados de interoperabilidad primarios (PIA) de Microsoft Office al instalar Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Para instalar los PIA al instalar Office

1. Asegúrese de que tiene una versión de .NET Framework que no sea anterior a la 2.0.

2. Instale Microsoft Office y asegúrese de que la característica **compatibilidad con programación de .net** esté seleccionada para las aplicaciones que desea extender (esta característica se incluye en la instalación predeterminada).

    > [!WARNING]
    > De forma predeterminada, los PIA se incrustan en la solución al compilarla, por lo que no tiene que distribuir los PIA a los usuarios como requisito previo para usar el complemento o la personalización de VSTO.

## <a name="see-also"></a>Vea también
- [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)
- [Cómo: Aplicaciones de Office de destino a través de ensamblados de interoperabilidad principales](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Cómo: Configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Cómo: Instalar el Visual Studio Tools para Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Información general sobre &#40;el desarrollo de soluciones de Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Introducción &#40;al desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
