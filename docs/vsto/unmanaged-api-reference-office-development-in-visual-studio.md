---
title: Referencia de la API no administrada (desarrollo de Office en Visual Studio)
ms.date: 08/14/2019
ms.topic: reference
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
ms.openlocfilehash: 4c1616d24ae9b2c072df4e5708eb98e86611a83d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540990"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referencia de la API no administrada (desarrollo de Office en Visual Studio)

A partir del sistema Microsoft Office de 2007, las aplicaciones de Office usan la interfaz de [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md) para llamar a un componente del cargador de complementos de VSTO que se incluye con [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Este componente se usa para ayudar a los complementos de VSTO administrados por carga. Puede crear su propio componente de cargador de complementos de VSTO implementando esta interfaz.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>En esta sección

[Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)

Una interfaz COM que se puede implementar para cargar y descargar complementos de VSTO administrados en las aplicaciones de Office.
