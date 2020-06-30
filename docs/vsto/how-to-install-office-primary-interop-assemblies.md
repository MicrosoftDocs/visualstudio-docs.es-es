---
title: 'Cómo: Instalar ensamblados de interoperabilidad primarios de Office'
ms.date: 08/14/2019
ms.topic: how-to
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
ms.openlocfilehash: b6f90b568f98abe5026525a60723efb59f737235
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544786"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Cómo: Instalar ensamblados de interoperabilidad primarios de Office
  Instale los ensamblados de interoperabilidad primarios (PIA) de Microsoft Office al instalar Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Para instalar los PIA al instalar Office

1. Asegúrese de que tiene una versión de .NET Framework que no sea anterior a la 2.0.

2. Instale Microsoft Office y asegúrese de que la característica **compatibilidad con programación de .net** esté seleccionada para las aplicaciones que desea extender (esta característica se incluye en la instalación predeterminada).

    > [!WARNING]
    > De forma predeterminada, los PIA se incrustan en la solución al compilarla, por lo que no tiene que distribuir los PIA a los usuarios como requisito previo para usar el complemento o la personalización de VSTO.

## <a name="see-also"></a>Consulte también
- [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)
- [Cómo: dirigirse a aplicaciones de Office a través de ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Cómo: configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Cómo: instalar el Visual Studio Tools para Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Introducción &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
