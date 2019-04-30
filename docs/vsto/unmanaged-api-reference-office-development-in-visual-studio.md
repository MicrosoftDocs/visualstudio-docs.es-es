---
title: Referencia de API no administrada (desarrollo de Office en Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 238ed42d48903d2d0ef26384245cff80785a8ebb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978242"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referencia de API no administrada (desarrollo de Office en Visual Studio)

A partir de 2007 Microsoft Office system, aplicaciones de Office usan la [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md) interfaz para llamar a un componente de cargador complementos de VSTO que se incluye con el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Este componente se utiliza para ayudar a administrada por carga de complementos VSTO. Puede crear su propio componente de cargador de complemento de VSTO implementando esta interfaz.

> [!NOTE]
> ¿Está interesado en desarrollar soluciones que amplían la experiencia de Office a través de [varias plataformas](https://dev.office.com/add-in-availability)? Visite el nuevo [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede crearlas con prácticamente cualquier tecnología, como HTML5, CSS3, JavaScript y XML de programación web.

## <a name="in-this-section"></a>En esta sección

[Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)

Una interfaz COM que se puede implementar para cargar y descargar complementos de VSTO administrados en las aplicaciones de Office.
